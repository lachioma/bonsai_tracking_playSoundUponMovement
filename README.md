# tracking_playSoundUponMovement


You can select the mode of mouse tracking out of 4 options, by enabling one of the following 4 nodes. Right-click a node to Enable/Disable.
- VelCentroid: use brightness threshold for mouse tracking; if velocity of centroid is above V, trigger sound playback; V is set using the node GreaterThan (a reasonable V is 5);
- VelCentroid_filt: same as before, but at each frame the median of the last 5 velocity points is taken;
- FrameDiff_nrPixels: use difference across consecutive frames to detect motion; if at least N pixels are different, trigger sound playback. N is set using the node GreaterThan (a reasonable N is ~150 (100-200)).
- FrameDiff_nrPixels_filt: same as before, but at each frame the median of the last 5 velocity points is taken.


Set sound card using CreateAudioContext.

Set sounds to play using AudioResources->Buffers and AudioResources->Sources.
Then change accordingly the sounds in PlaySource, PauseSource, and RewindSource.

CropPolygon allows you to select a subregion of the whole frame to use for mouse tracking.
To draw/modify the ROI, first run the routine; then select CropPolygon and click the button "..." to the right side of Regions; a window titles "Regions" opens, use the following commands:
- drag and drop with left click inside the ROI to shift the entire ROI;
- left click outside the ROI create an additional, distinct ROI;
- use double-click inside the ROI, close to an edge, to add a point to the polygon;
- drag and drop using right click inside the ROI to move the point (the point nearest to the mouse cursor will be moved); 
- double-click with right click will delete the point (the point nearest to the mouse cursor will be deleted);
- use Tab to move selection across multiple ROIs
- use Delete to delete the selected ROI;
- use Ctrl+Z to undo;
Close the window "Regions" when you are done.

In Threshold, use the property ThresholdValue to set the gray value (out of 255) below which we look for contours, i.e. the mouse must be darker than this value and ideally only the mouse.

In FindContours, use MaxArea and MinArea to define area costranints for the mouse ROI that will be detected at each frame.

In BackgroundSubtraction, use the property ThresholdValue to set the gray value (out of 255) used to distinguish foreground and background: count only the pixels that have a delta gray value between consecutive frames above the ThresholdValue.


![Screenshot 2023-03-27 165814](https://user-images.githubusercontent.com/29898879/228065197-7aea72cd-d0a2-4d3d-a871-cd01eed74aac.png)
![Screenshot 2023-03-27 165840](https://user-images.githubusercontent.com/29898879/228065230-b5891c94-7979-4fda-9a28-6018b57399c1.png)
