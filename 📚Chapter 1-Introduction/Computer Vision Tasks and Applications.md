


## 📑 Table of Contents  

- [Content Recognition](#Content-Recognition)  
- [What is Computer Vision?](#2--what-is-computer-vision)  
- [What is Computer Vision NOT?](#what-is-computer-vision-not)  
- [How does Computer Vision work?](#3-how-does-computer-vision-work)
- [Real life Example?](#Real-life-Example)   
- [History of Computer Vision](#history-of-computer-vision)  


## **Content Recognition** 
### **1.1-Image Classification** 

Image classification is one of the main tasks in the field of computer vision [1].In this task, the trained model assigns a certain class to the image based on a predefined set of classes. The figure below is the famous CIFAR-10 dataset [1], which consists of 80 million images of ten classes. In the image classification task, the model is trained to assign the input image to one of the predefined ten classes, as shown in the figure below.
The computer analyzes an image in the form of pixels. It does it by considering the image as an array of matrices with the size of the matrix reliant on the image resolution. Put simply, image classification, in a computer’s view, is the analysis of this statistical data using algorithms. In digital image processing, image classification is done by automatically grouping pixels into specified categories, so-called classes. The algorithms segregate the image into a series of its most prominent features, lowering the workload on the final classifier. These characteristics give the classifier an idea of what the image represents and what class it might be considered into. The characteristic extraction process makes up the most important step in categorizing an image, as the rest of the steps depend on it.

<p align="center">
<img src="https://github.com/dr-mushtaq/Computer-Vision/blob/main/%F0%9F%93%9AChapter%201-Introduction/1_r8S5tF_6naagKOnlIcGXoQ.png"></a>
</p>

**Image classification applications**:

There are a lot of real-world applications for image classification [1].

**Automated inspection and quality control**: Image classification can be used to automatically inspect products on an assembly line and identify those that do not meet quality standards.

<p align="center">
<img src="https://github.com/dr-mushtaq/Computer-Vision/blob/main/%F0%9F%93%9AChapter%201-Introduction/1_C_NE-EiDssUNEwFAeRAdMA.jpg"></a>
</p>

**Classification of skin cancer**: Another application of image classification in the healthcare domain is automating the classifying of skin images into malignant and begin.

<p align="center">
<img src="https://github.com/dr-mushtaq/Computer-Vision/blob/main/%F0%9F%93%9AChapter%201-Introduction/1_sw03jwLc830SfOYmYSP3Dw.png"></a>
</p>

**Land use mapping**: Image classification can be used to automatically map land use and identify different land types.
**Security and Medical Imaging**: Finally, two more surveillance is a huge issue. This ideas of being able to monitor environment for crowd safety, a variety of reasons.

<p align="center">
<img src="https://github.com/dr-mushtaq/Computer-Vision/blob/main/%F0%9F%93%9AChapter%201-Introduction/333.jpg"></a>
</p>

These are screenshots taken from Siemens sells a system for doing port monitoring.Just to know whether, say, people are loitering, or vehicles are approaching that aren't supposed to be. This is also a computer vision. A more direct effect on a single individual with computer vision is work in medical imagining. Okay, so here you see an example. There's all sorts of 3D imaging, MRI, CAT scan, stuff like that, but here you see some work.This came out of Eric Grimson's lab a while ago at MIT where on a screen, a the computer vision system is registering the skull that's on the table with a model that has been created from the 3D imaging. So while, when the surgeon looks at this monitor, he sees the real person, and by the way, if there were a scalpel here, he'd see the hand with the scalpel or drill or whatever you're using to make a hole in the person's head. And where the various structures are underneath that you wanted to see, and that's also computer vision.

<p align="center">
<img src="https://github.com/dr-mushtaq/Computer-Vision/blob/main/%F0%9F%93%9AChapter%201-Introduction/444.jpg"></a>
</p>



 # **Object Identification**
As mentioned, image classification works by assigning classes or labels to the picture from a predefined set of labels, object identification recognizes specific instances of the class. For example the image classification tasks, the focus is to classify the face's pictures, in object identification, the focus is on identifying the person and recognizing them. Therefore, object detection can be seen as a clustering algorithm to cluster similar instances with each other.

## **Object Detection and Localization** 

Sometimes we also need to extract the location of an object that is present in the image. This is when we can use Object Detection, another well-known and useful Computer Vision task 

<p align="center">
<img src="https://github.com/dr-mushtaq/Computer-Vision/blob/main/%F0%9F%93%9AChapter%201-Introduction/7.png"></a>
</p>
 
Here instead of just the label, the system also provides you with bounding box coordinates to tell where exactly the object is located in the image.
<p align="center">
<img src="https://github.com/dr-mushtaq/Computer-Vision/blob/main/%F0%9F%93%9AChapter%201-Introduction/8.png"></a>
</p>

Another important task of content recognition is object detection. Object detection is the task of detecting instances of objects of a certain class within an image. Object detection is often a preliminary task before further computations, such as in facial recognition, in which you have to detect the faces first and crop it before recognition 

<p align="center">
<img src="https://github.com/dr-mushtaq/Computer-Vision/blob/main/%F0%9F%93%9AChapter%201-Introduction/1_alePWgdMrQeS7-WBVd0MVA.png"></a>
</p>

There are many industrial use cases of classification systems and their variations. A popular application is Facial Recognition. Where a computer program can recognize and identify the people in images by analyzing their faces. Facial Recognition is used almost everywhere from employee attendance to unlocking mobile phones.

<p align="center">
<img src="https://github.com/dr-mushtaq/Computer-Vision/blob/main/%F0%9F%93%9AChapter%201-Introduction/3.png"></a>
</p>
It’s even used by Facebook to tag people, It identifies people in uploaded images/videos and automatically suggests to tag them if they’re in your mutual friends, etc .

<p align="center">
<img src="https://github.com/dr-mushtaq/Computer-Vision/blob/main/%F0%9F%93%9AChapter%201-Introduction/4.jpeg"></a>
</p>

Another thing that's very common these days is face detection. Just about any digital camera that you buy today, you pick it up, using the default setting, it will find the faces. So, here's an example. One of the cool things, by the way, is bunch of lectures in the future, we'll talk about the technology that basically does exactly this. So the next time, so when we get to those, you pick up a camera and it finds the faces. You'll say, oh, I know how they're doing that. But actually now, cameras can do more. I think the one on the left, I think is from the web, from Fiji, that if you take a picture of somebody, and they blink. You know, and that can be really annoying, it'll tell you they blinked. Maybe even more interestingly, Sony has something called the Smile Shutter, which will watch for people. And you sort of press it, and say, take a picture now. But actually it waits until you, it sees the person smile. And even further these days, there are cameras that will recognize who you are. So this is a screen taken from a shot where it does camera based login. So it knows about a bunch of different people. You walk up to the computer, you say, yo, computer it's me. Actually you don't have to say anything, and the computer says, it's you. And it logs you in. So that's face recognition. We're going to talk also, a little bit, about face recognition. Although the face detection stuff techno, that technology is one that will be sort of more fundamental to the class .
<p align="center">
<img src="https://github.com/dr-mushtaq/Computer-Vision/blob/main/%F0%9F%93%9AChapter%201-Introduction/5.png"></a>
</p>

## Object detection application:
Object detection is one of the most used computer vision applications in real life. It has been applied in most of the domains, such as [1]:

Danger detection in security and surveillance: A wide range of security applications in video surveillance are based on object detection, for example, to detect people in restricted or dangerous areas, suicide prevention, or automating inspection tasks in remote locations with computer vision.
Vehicle detection with AI in Transportation and logistics domain: Object detection is used to detect and count vehicles for traffic analysis or to detect cars that stop in dangerous areas, for example, on crossroads or highways.

### References

1-[What is Computer Vision? & Its Applications](https://medium.com/@draj0718/what-is-computer-vision-its-applications-826c0bbd772b)

2-[-Introduction of Computer Vision](https://auth.udacity.com/sign-in)

4-[How computer vision works](https://www.sas.com/en_us/insights/analytics/computer-vision.html#technical)

5-[Computer Vision 🤖 Fundamentals with OpenCV](https://medium.com/codex/computer-vision-fundamentals-with-opencv-9fc93b61e3e8)


<p align="right">
  <a target="_blank" href="https://coursesteach.com/mod/page/view.php?id=3962">
    <img height="50px" src="https://raw.githubusercontent.com/dipanjanS/practical-machine-learning-with-python/master/media/assets/home_page.png" />
  </a>
  <a target="_blank" href="https://coursesteach.com/course/view.php?id=6&amp;sectionid=30">
    <img height="50px" src="https://raw.githubusercontent.com/dipanjanS/practical-machine-learning-with-python/master/media/assets/contents_page.jpg" />
  </a>
  <img height="50px" src="https://raw.githubusercontent.com/dipanjanS/practical-machine-learning-with-python/master/media/assets/next_page.png" style="float: right;" />
</p>

# <span style="color: #ff0000;"><strong><span style="font-size: x-large;"><span style="font-family: arial, helvetica, sans-serif;">Practical Machine Learning with Python</span></span></strong></span>






































