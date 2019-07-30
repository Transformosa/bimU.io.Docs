# Nagivate Using Web Viewer

Some introduction here...

![Screenshot](images/placeholder.jpg){: class="center" style="width:300px"}

## Use 3D Viewer

bimU.io's 3D viewer is web-based, which means that it is cross-platform and can be used on any device as long as you have a WebGL-enabled browser installed. We suggest use the latest version of Google Chrome to achieve the best performance.

![Screenshot](images/placeholder.jpg){: class="center" style="width:300px"}

The viewer toolbar is located at the bottom of the 3D viewer. The status labels will be shown on the bottom left when you make changes, such as enabling sectiong, selecting elements, changing element visibility, etc.

### Basic Viewer Controls

You can control the camera with the following tools to view the 3D scene from different perspectives.

- **Orbit:** The orbit tool allows you to rotate the camera around your model by using left mouse drag on desktop or one finger swipe on mobile devices. The camera will orbit around the centre of current selection or the previous zoom target. 
- **Pan:** The pan tool allows you to move the camera vertically or horizontally by using right mouse drag on desktop or two-finger scroll on mobile devices.
- **Zoom:** The zoom tool allows you to zoom in to focus on a specific area or zoom out to see more of your model by using the mouse wheel on desktop or two-finger pinch on mobile devices. The zoom speed will decrease gradually as the camera gets closer to the zoom target.

### Specfic Camera Viewpoints

 You can use the following tools to set camera viewpoint to specific areas you want to see.

- **Zoom to Fit:** This tool fits the entire model into the current viewport. It is particularly useful when you get lost in the 3D scene.
- **Zoom to Selection:** This tool fits the selected elements into the current viewport to focus on them. You can use this tool if a target is too far or too close to zoom. 
- **Open Viewpoint:** This tool opens the camera viewpoint attached to a markup in either bimU.io's 3D viewer or BIM software. See more details [here](#work-with-markups). 
- **Rotate View:** This tool can view your model from all sides of the bounding box, including top, bottom, front, back, left, and right.

### Section Cut

You can enable sectioning to slice your model to view more details inside. To disable sectioning, use the _Reset Visibility_ tool.

- **Section Box:** This tool cuts model geometry by a rectangular box. The six edges of the section box can be adjusted using the grips.
- **Section around Selection:** This tool creates a section box around the selected elements. Then you can expand it to view the adjacent area.

### Model Elements

- **Select Elements:** Use left mouse click to select a model element. Shift + Left click to select multiple elements.
- **Hide Elements:** This tool hides the selected elements. You can use the _Reset Visibility_ tool to unhide them.

### Other Viewer Capabilities

- **Reset Visibility:** This tool unhides all hidden elements and disables sectioning.
- **Measuring Tool:** A few different measurement tools are available, such as reporting coordinates, measuring distance, height, angle, area, etc.
- **Toogle Fullscreen:** This tool presents the entire viewport of the 3D viewer in browser's fullscreen mode.
- **Use Orthographic Camera:** This tool can switch the camera between perspective and orthographic projection.
- **Switch to Embedded Mode:** This tool enables the embedded mode which isolates the 3D viewer from the user interface. You can still view BIM data from the toolbar. It is particularly useful when the fullscreen mode is not supported, such as iOS devices.

## Work with Markups
What is a markup?

### Create a Markup

### View a Markup
Can edit description, download image, delete.

### Open Viewpoint in Web Viewer

### Open Viewpoint in BIM Software
		
## View BIM Data

### Model Tab

### Element Tab

### File Tab

## Mobile User Interface

A simplified user interface will be enabled on a mobile device if the screen size is too small. You can still view BIM data from the toolbar though some of the tools might be disabled. The main user interface might be available if you change device orientation to landscape mode and then refresh the entire page.