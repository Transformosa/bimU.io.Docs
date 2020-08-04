# Authentication

### Access Token
bimU.io Viewer API uses token-based authentication that is secure, reliable, and compliant with the prevailing JWT mechanism. A one-time access token must be generated to load a model or retrieve information from the bimU.io platform. The generated access token is valid for two hours only.

There are two ways to generate an access token: **API key** or **model password**. Using model password is easier. However, it is recommended to use API key that is a more robust and flexible approach. 

### Using API Key
Every bimU.io user has a corresponding account name and can generate an API key which is unique to the bimU.io account. You can find your account name and generate an API key on bimU.io by going to **Settings** => **API Key**. All your models are programmatically accessible by a generated API key even though they are not shared explicitly. Therefore, please bear in mind the following best practices:
- Use environmental variables rather than putting your account name and API key directly in code.
- Never check in an API key to your source code repositories.
- Do not use an API key in a front-end web application.
- Do not share an API key with others.
- Revoke an API key in case of any security risk.

A back-end, server-side web application should be set up to use an API key to request for an access token. You need to put together your account name (as user ID) and API key (as password) for the HTTP Basic Authentication. An HTTP request can then be sent to the REST API endpoint below.

**HTTP Request for Access Token**
```
POST /rest/api/v1/token HTTP/1.1
Host: viewer.bimu.io
Authorization: Basic xxxxxxxxxxx
```

**Sample Response**
``` json
{
    "token": "eyJhbGciOiJIUzI1NiJ9.eyJpYX......"
}
```

A couple of server-side code examples are provided below if you use Node.js (JavaScript) or .NET Core (C#) for the back-end web application.

**Node.js Request Example**
``` javascript
let request = require('request');

let accountName = "YOUR_ACCOUNT_NAME";
let apiKey = "YOUR_API_KEY";
let base64Encoded = Buffer.from(`${accountName}':'${apiKey}`).toString('base64');

let options = {
  'method': 'POST',
  'url': 'https://viewer.bimu.io/rest/api/v1/token',
  'headers': {
    'Authorization': `Basic ${base64Encoded}`
  }
};
request(options, function (error, response) {
  if (error) throw new Error(error);
  let accessToken = JSON.parse(response.body).token;
  console.log(accessToken);
});

```

**C# RestSharp Example**
``` c#
using RestSharp;
using RestSharp.Serialization.Json;
using System;
using System.Text;

namespace ConsoleApp
{
    class Program
    {
        static void Main(string[] args)
        {
            var accountName = "YOUR_ACCOUNT_NAME";
            var apiKey = "YOUR_API_KEY";

            var client = new RestClient("https://viewer.bimu.io/rest/api/v1/token");
            var request = new RestRequest(Method.POST);

            Byte[] bytesEncoded = Encoding.UTF8.GetBytes($"{accountName}:{apiKey}");
            string base64Encoded = Convert.ToBase64String(bytesEncoded);

            request.AddHeader("Authorization", $"Basic {base64Encoded}");
            IRestResponse response = client.Execute(request);
            var accessTokenResponse = new JsonDeserializer().Deserialize<AccessTokenResponse>(response);
            Console.WriteLine(accessTokenResponse.token);
        }
    }

    class AccessTokenResponse 
    {
        public string token { get; set; }
    }
}
```

Once an access token is received like the sample response above, you can pass it on to a front-end web application for the model configuration object. An example below shows how to load a model by an access token.

``` javascript
// Model configuration object
let modelConfigs = {
    modelId: "YOUR_MODEL_ID",
    accessToken: "ACCESS_TOKEN"
};

// Load a model
viewer.loadModel(modelConfigs, onPorgress, onLoaded, onError);
```

### Using Model Password
If working with a back-end web application is a challenge, then using model password is your best bet. A model password is specific to a model file. You must explicitly share a model on bimU.io to make it accessible by bimU.io Viewer API. If you don't set a password upon sharing, the password property of the model configuration object can be set to null or an empty string.

If a model password is specified in the model configuration object like below, the loadModel function will handle access token request behind the scene and load the model directly. Please do not hard code your password in a front-end web application unless it is hosted in a fully trusted environment, such as intranet. 

``` javascript
// Model configuration object
let modelConfigs = {
    modelId: "YOUR_MODEL_ID",
    password: "YOUR_MODEL_PASSWORD"
};

// Load a model
viewer.loadModel(modelConfigs, onPorgress, onLoaded, onError);
```

Ideally, you should create your own user interface and prompt your users to input a password. bimU.io Viewer API has got a helper function called ```showDialog``` that comes in quite handy. See an example below.

``` javascript
let onSubmit = () => {				
    viewer.closeDialog();
    let password = document.getElementById("password-input").value;
    let modelConfigs = {
      modelId: "YOUR_MODEL_ID",
      password: password
    };
    viewer.loadModel(modelConfigs, onPorgress, onLoaded, onError);
};
let modalTitle = "Protected Content";
let modalBody = `
  <div>Input password</div>
  <div style="margin-top: 15px;">
    <input style="padding: 10px;border: 1px solid #ccc;border-radius: 4px;" placeholder="Enter your password here" id="password-input" type="password" class="validate">
  </div>
`;
viewer.showDialog(modalTitle, modalBody, null, "OK", onSubmit, false);
```