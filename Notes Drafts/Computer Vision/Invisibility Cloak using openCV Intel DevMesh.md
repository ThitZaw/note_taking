# Invisibility Cloak using openCV | Intel DevMesh

[https://devmesh.intel.com/projects/invisibility-cloak-using-opencv](https://devmesh.intel.com/projects/invisibility-cloak-using-opencv)

The project is based on computer vision. Specifically this is built with openCV.

By segmenting a single predefined color from a video footage and replacing it with a preexisting same background, we can create the immersion of invisibility cloak. Like the one used in Harry Potter.

### Methodology / Approach

1.  

    First a color to be segmented out is chosen.

2.  

    The background without the subject(that is to become seemingly invisible) is captured.

3.  

    The color space of the feed of the camera is converted from BGR to HSV

4.  

    The video footage is segmented to create masks with upper and lower threshold values of the color to be segmented.

5.  

    The segmentation process is done via creating masks with a range of Hue Saturation and Brightness value of the segmentation color.

6.  

    The segmented mask is refined for better performance via morphologyEx of openCV.

7.  

    Another inverted mask is generated from the above mask by performing bitwise not operation.

8.  

    Bitwise and operation is performed on the background and the mask to get resultant mask 1.

9.  

    Similarly bitwise and operation is performed on the video feed images and the inverted mask to get resultant mask 2

10.  

    Both the resultant masks are added via Linear Blend, i,e, the addWeighted method of openCV

11.  

    Finally the output of the blend is displayed.

### Technologies Used

openCV

python

intel RealSense

Intel Inside: Intel Python

- 

    [Invisibility%20Cloak%20using%20openCV%20Intel%20DevMesh/thumb_6c233b61-5518-4550-841d-98735264b689](Invisibility%20Cloak%20using%20openCV%20Intel%20DevMesh/thumb_6c233b61-5518-4550-841d-98735264b689)