---
title:  IPyWidgets v Dash for GUI Image Processing
date: 2023-12-02
image:
  focal_point: 'top'
authors: ["david_costello", "admin"]
---

### Introduction

During Summer 2023, I was working on a research project. I was trying to create a piece of software that would allow the user to take in a Greek Manuscript, like [this one](https://digital.bodleian.ox.ac.uk/objects/403c2c20-5072-4ad2-831d-a43edbdfcf47/surfaces/ec0c1ff3-8d5a-4d55-bcc5-5a02963adc34/), and then, using the software, produce a computer-generated transcription of the text inside, a classic [Optical Character Recognition problem](https://en.wikipedia.org/wiki/Optical_character_recognition). Because there's not just one set of tools to do this work, I wanted to collect them all under one software umbrella. In theory, it would be an end-to-end experience that would allow users to process images for an OCR engine, like [Tesseract](https://en.wikipedia.org/wiki/Tesseract_(software)), to both train on and transcribe without the software user having to ever write a single line of code. Therefore, it seemed best to create a Graphical User Interface so that users could actually 'interact' with images through the software while using Python code to do the computational work needed. In order to create the GUI using Python, I needed a simple library that could do a lot of the heavy lifting for me. That's why I started programming with the IPyWidgets library.

### IPyWidgets
There were a lot of reasons to use the [IPyWidgets](https://ipywidgets.readthedocs.io/en/stable/) library. Using IPyWidgets, I could create a GUI that would run on pretty much any system that was able to run an internet browser. This is because IPyWidgets is built off of the main languages for Web Development: JavaScript, HTML, and CSS. Several things that are done by these languages are wrapped for Python use in the IPyWidgets library and are able to run with a live Python kernel, meaning that users can click buttons and tweak some sliders while a Python script can take those changes as inputs and give the user an immediate result. This means that IPyWidgets is a wonderful plug-and-play library for developers who are new to GUI development, which I was at the time. However, there were some hiccups.

#### Model View Controller Digression

> One of the most common patterns for developing software applications with a graphical interface is the Model-View-Controller ( or MVC) pattern. Any application developed with this pattern in mind separates the application into three components with different purposes. The *model* handles data structures and data manipulations. The *view* is what the user sees and interacts with. The *controller* is the part of the application that allows the model and the view components to communicate with each other, sort of like a switchboard operator receiving a call and making sure the right recipient is connected to it. An example would be a video game where users, viewing a gameplay scenario, input commands to move a character and the model, ordered by the controller, updates the view after doing the necessary computation to change what the environment looks like during movement. If you want to learn more about this software pattern, you can start [here](https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller).

The centerpiece of my application is the interactive image processing. Python has several libraries which are good for non-interactive image processing such as [OpenCV](https://opencv.org/) and [PIL](https://pillow.readthedocs.io/en/stable/). Beyond the functionality in these libraries, I wanted users to be able to draw a line over text in a manuscript image and then associate the coordinates of that line with a manual transcription to create training data for Tesseract to use. <!---**[THIS IS WHERE AN IMAGE IS NEEDED]** --> Using the model-view-controller pattern, I wanted the lines drawn over the image, as a change in view, to be connected to the controller that could then cause a change in the model to store data. However, this was not possible with IPyWidgets. There is [a widget](https://ipywidgets.readthedocs.io/en/stable/examples/Widget%20List.html#image) in the IPyWidgets library that displays an image but does not allow users to draw on the image. There was an [interactive graph element](https://holoviews.org/reference/streams/bokeh/BoxEdit.html) compatible with IPyWidgets that could be hooked into the application controller that could theoretically use an image as a background element, but, due to an unfixed bug, I could not make the element work. After trying out multiple different libraries, I settled on [Dash](https://dash.plotly.com/) because it had a [robust web element](https://dash.plotly.com/annotations) capable of allowing users to annotate images and accessing that annotation with the application controller while the application was running. So I needed to learn the new library.

### Dash

Dash is owned and maintained by Plotly, a company that makes its money by selling licenses for the Enterprise version of Dash. Because of this, Dash is a very well maintained library that has limited integrations with other Python libraries. Unfortunately, IPyWidgets is not one of the libraries compatible with Dash. Though Dash is similar to IPyWidgets, in that it wraps HTML, JavaScript, and CSS for use in Python scripts, it has some differences. One big difference is that an application built using Dash has to run on a server, whether that is a local server or a remote server. Further, Dash is meant to be used with a *stateless* approach for web applications. In abstract, a web application built with a stateless approach is run on a server where the server processes user requests and input and returns an output without the server saving any of the data sent by the user or any of the output generated by the server. In practice, this stateless approach meant that Dash did not handle global variables in Python very well and it required a few creative workarounds. Considering that I was trying to create locally stored data using my application, the lack of saving within the server proved to be very difficult to work with. All of the code I had already developed needed to be ported over into the Dash context.

#### Dash Application Digression

> When developing a Dash application, it's worth knowing the anatomy of what the code will look like. There are roughly four sections. I will refer to them as **imports**, **layout**, **controls**, and **running**. The imports section is exactly what it sounds like, the section containing all of the library import statements. The running section is not very complicated either. It contains a statement that deploys a server and runs the application on it with options for development. The more complicated sections are the layout and controls sections. The layout section is where all the components of the view, the user interface, are instantiated as Python objects and put into a visual layout. This is where buttons, boxes, images, tabs, and all the other components of the interface are defined in a way very similar to HTML. Every time a component is defined in the layout section, it can be given an id. This id is how the component is tracked for the controller. The controls section is where user interactions with components are tracked, providing interactivity for the user. It really is where the controller and model of the model-view-controller pattern are coded. This is done using [callback functions](https://en.wikipedia.org/wiki/Callback_(computer_programming)) that are linked to components in the view via the component id defined in the layout section. Whenever a change is made to a component tracked by a callback function, which could be caused by a user input or as a result of another callback function, the callback function is called automatically, giving feedback and interactivity to the user. For more documentation, start [here](https://dash.plotly.com/minimal-app).

There were two main problems that I had when porting my pre-existing code to the stateless environment. The first is that all callback functions in Dash, the code for the MVC controller, require at least one output component to be named and, therefore, updated whenever the callback runs. This was problematic because my application included save buttons that would take user input (from the image annotation and transcription) and store it to a local file. There was no obvious 'output' in the view. So, I made a dummy output component. 

- global variables to avoid forcing updates and callbacks
- dummy output for callbacks not intended to affect the view


### Dash vs. IPyWidgets

##### Why Dash over IPyWidgets?

- Dash had a useful widget that I needed while IPyWidgets did not
- IPyWidgets is more restrictive in its layout and styling
- Dash is privately maintained, so many elements of it are likely to just work together

##### Why IPyWidgets is still worth considering

- The Python focus is more in line with certain use cases, especially in research contexts, where the stateless paradigm is unnecessarily obtuse and, in fact, difficult to program with it in mind
- Dash is a walled garden in some sense, keeping its integrations pretty tightly controlled while IPyWidgets has a lot of possible interconnections that Dash just doesn't
- IPyWidgets is a fine enough library and, for individuals only familiar with Python, it is quite easy to pick up and play with as long as you have a little guidance or tenacity.

