---
title:  How the Little Jupyter Notebook Became a Web App
subtitle: Managing Increasing Complexity with nbdev

event: SciPy 2023
event_url: https://cfp.scipy.org/2023/talk/NFWZXD/

location: 'Austin, TX'

summary: In this tutorial we walk through what it takes to transform an exploratory Jupyter Notebook into a mature web application

abstract:  Already familiar with ipywidgets, but ready to take your skills to the next level? In this tutorial we walk through what it takes to transform an exploratory Jupyter Notebook into a mature web application. Web apps can be a valuable product of collaboration between researchers and software developers, and the packages used in this tutorial were selected to support this relationship, starting with using JupyterLab as an integrated development environment. Attendees will learn how to design and document a scientific web application that accommodates increasing complexity, but is also inheritable by the researchers who maintain them in the long run.


# Talk start and end times.
#   End time can optionally be hidden by prefixing the line with `#`.
date: '2023-07-10'
#date_end: '2030-06-01T15:00:00Z'
#all_day: false

# Schedule page publish date (NOT talk date).
publishDate: '2024-02-11'

authors: ['Nicole Brewer', 'Ludovico Bianchi']
tags: ['web-application', 'data-dashboard', 'ipywidgets', 'interactive']

# Is this a featured talk? (true/false)
featured: true

#image:
#  caption: 'Image credit: [**Unsplash**](https://unsplash.com/photos/bzdhc5b3Bxs)'
#  focal_point: Right

url_code: 'https://github.com/nicole-brewer/scipy23-jupyter-web-app-tutorial'
url_pdf: ''
url_slides: ''
url_video: ''

# Markdown Slides (optional).
#   Associate this talk with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides = "example-slides"` references `content/slides/example-slides.md`.
#   Otherwise, set `slides = ""`.
#slides:

# Projects (optional).
#   Associate this post with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `projects = ["internal-project"]` references `content/project/deep-learning/index.md`.
#   Otherwise, set `projects = []`.
#projects:
---

## About

Already familiar with ipywidgets, but ready to take your skills to the next level? In this tutorial we walk through what it takes to transform an exploratory Jupyter Notebook into a mature web application. Web apps can be a valuable product of collaboration between researchers and software developers, and the packages used in this tutorial were selected to support this relationship, starting with using JupyterLab as an integrated development environment. Attendees will learn how to design and document a scientific web application that accommodates increasing complexity, but is also inheritable by the researchers who maintain them in the long run.

## The Story of the Little Notebook

Our tutorial should appeal to scientists and software developers alike. We hope to convince you that web applications are excellent tools for improving the accessibility of scientific data and software and provide you with the know-how to develop one that accommodates growth and collaboration. The structure of the tutorial is based on a true story about a little Jupyter Notebook…

One day, a research scientist created the Notebook to do some exploratory development. After a while, that Notebook grew into a reusable workflow for creating a helpful visualization the scientist often ran for different parameters. The scientist eventually recognized that their workflow might be worth sharing, so they started working with a software developer to help the little Notebook grow into a web application. At first, the developer replaced hardcoded inputs into interactive ipywidgets, and used Voila` to hide the code cells from users. That was the day the little Notebook became a dashboard, but its journey didn’t stop there. Over time, the researcher had new ideas about features they wanted to add, so the developer transformed the dashboard into a tab-based web application that could accommodate more steps with rich instructions.

But there was a problem. The Notebook started experiencing growing pains. It contained more code than was comfortable. The developer made the notebook feel better by offloading some of the code into python modules. This worked well for logic, but as the application grew more complex, it was important to develop nested widget components in the visual Notebook environment. At first, the developer coded views in extra notebooks, and then copy-pasted the code into the python module, but this became laborious and confusing. One day, the developer started to write a tool that would export code cells from the notebooks into python modules. That way, the developer could code entirely in notebooks, and they could leave in all the markdown and code cells that documented what they were thinking as they designed the tool. That was the day that the little Notebook became a literate Notebook family.

Not long after, the developer was listening to the Talk Python to Me podcast, and heard someone mention a tool called nbdev. The tool was just like the one the developer had made, except it had many more useful features, like notebook-friendly git commits and merges. Eureka! Finally, the developer could accommodate increasing complexity with simple tools. When the developer gave the Notebook family back, the researchers were able to maintain it themselves, without having to download scary IDEs, extensions, or environments. And they all lived happily ever after.

## Prerequisites

Prior exposure to ipywidgets and/or familiarity with object-oriented programming is recommended. We review the basics of ipywidgets within the first hour and quickly move on to more advanced design principles.

