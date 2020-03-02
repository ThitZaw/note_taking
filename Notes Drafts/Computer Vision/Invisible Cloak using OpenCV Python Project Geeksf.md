# Invisible Cloak using OpenCV | Python Project - GeeksforGeeks

[https://www.geeksforgeeks.org/invisible-cloak-using-opencv-python-project/](https://www.geeksforgeeks.org/invisible-cloak-using-opencv-python-project/)

Have you ever seen Harry Potter’s Invisible Cloak; Was it wonderful? Have you ever wanted to wear that cloak? If Yes!! then in this post, we will build the same cloak which Harry Potter uses to become invisible. Yes, we are not building it in a real way but it is all about graphics trickery.

In this post, we will learn how to create our own ‘Invisibility Cloak’ using simple computer vision techniques in **OpenCV**. Here we have written this code in Python because it provides exhaustive and sufficient library to build this program.

Here, we will create this magical experience using an image processing technique called **Color detection and segmentation**. In order to run this code, you need an mp4 video named “`video.mp4`“. You must have a cloth of same color and no other color should be visible into that cloth. We are taking the red cloth. If you are taking some other cloth, the code will remain the same but with minute changes.

**Why Red? Green is my favorite?** Sure, we could have used green, isn’t Red the magician’s color? Jokes aside, colors like green or blue will also work fine with a little bit of changes in code. This technique is opposite to the **Green Screening**. In green screening, we remove background but here we will remove the foreground frame. So let’s start our code.

**Algorithm:**

> 1. Capture and store the background frame [ This will be done for some seconds ] 2. Detect the red colored cloth using color detection and segmentation algorithm. 3. Segment out the red colored cloth by generating a mask. [ used in code ] 4. Generate the final augmented output to create a magical effect. [ video.mp4 ]

**Below is the Code:**

[Untitled](Invisible%20Cloak%20using%20OpenCV%20Python%20Project%20Geeksf/Untitled%20Database.csv)

**Output:**

You can check source code on the project github repository, for input video and more details – [here](https://github.com/AdityaAtri/invisible_man.git)

**Reference:**  [http://datasciencenthusiast.com/?p=71](http://datasciencenthusiast.com/?p=71)