---
title: 10,000 Foot View of Jupyter4Science
author: "admin"
date: '2024-02-27'
slug: 10000-foot-view
categories: []
tags: []
subtitle: ''
summary: 'In this post we give a 10,000 foot view of the kind of content you can expect to see on Jupyter4Science. Before getting into individual topics, we will review what Jupyter Notebooks are, how they are most commonly used in the context of research, and what value of Jupyter Notebooks in collaborative settings.'
authors: []
lastmod: '2024-02-27T23:02:44-07:00'
featured: no
image:
  caption: ''
  focal_point: ''
  preview_only: no
projects: []
---

The purpose of this post is to give you, the reader, a 10,000 foot view of the kind of content you can expect to see on the site. Before getting into individual topics, we will review what Jupyter Notebooks are, how they are most commonly used in the context of research, and what value the Jupyter notebook format brings to the table.

### Jupyter Notebook and the Jupyter Ecosystem
Computational notebooks come in many varieties, but they all have one thing in common: much like traditional laboratory notebooks, computational notebooks contain code cells interspersed with text that can be used to explain and narrate their analysis. Jupyter Notebook is one such format of a computational notebook (files ending in the extension `.ipynb`), but the term also refers to the classic browser-based interface that is used to create such documents.

{{< figure src="1000-foot-view.png" >}}

Jupyter Notebook is just one of many projects, like JupyterLab and Jupyter Widgets, at the core of the broader open-source ecosystem, all of which are used in reseach.

### Jupyter Notebooks as Computational Workflows

In research settings, Jupyter Notebooks are often used to create and share procedural documents called **computational workflows**, which document data sources, steps in analysis, mathematical calculations, and findings. Jupyter Notebooks, which support code cells in many languages, markdown, and LaTeX, often comprise the entire workflow from data input to graphical result. However, notebooks can also represent a single step in a much larger research workflow which is coordinated on a supercomputer.

### The Value Proposition of Jupyter Notebooks a Tools Collaboration
Jupyter can be ideal platform for development in collaborative settings where computational scientists, research software engineers, academic data scientists, and other research computing and data (RCD) professionals collaborate with researchers who often are expected to inherit and maintain the code in the long run. 

## Topics you can expect to see on Jupyter4Science

The [Jupyter4Science]({{< ref "/" >}}) site is both a blog and set of curated resources about developing, reproducing, sharing, and publishing Jupyter Notebooks in a research setting. This site was a product of a [Better Scientific Software fellowship ](https://bssw.io/fellows/nicole-brewer), which aimed to improve accessibility of research data and software through a lesser-known known use of Jupyter Notebooks: scientific web applications. The content of the site has since expanded to include a broader array of resources, including blog posts, templates, example notebooks, tutorials, publications, podcast episodes, and more. Topics include...

- [Notebooks as Computational Workflows](#notebooks-as-computational-workflows)
- [Development Environments for Jupyter Notebooks](#Development-Environments-for-Jupyter-Notebooks)
- [Reproducible Environments](#Reproducible-Environments)
- [Sharing Notebooks](#Sharing-Notebooks)
- [Creating Publications with Quarto](#Creating-Publications-with-Quarto)
- [Templates and Best Practices](#Templates-and-Best-Practices)
- [Jupyter Notebooks as Peer-Reviewed Objects](#Jupyter-Notebooks-as-Peer-Reviewed-Objects)
- [Building Data Dashboards and Web Applications with Jupyter Notebooks](#Building-Data-Dashboards-and-Web-Applications-with-Jupyter-Notebooks)


### Development Environments for Jupyter Notebooks

There are many development environments one could choose to edit Jupyter Notebooks in. A plain text editor like "TextEdit" on Mac and "Notepad" on Windows is not one of them, because under the hood, Jupyter Notebook files actually contain a whole bunch of JSON. Though these files are technically human-readible, they are very difficult to look at.

<!--?picture-->

But no fear, there are many environment choices that are suitable for developing Jupyter Notebooks. Perhaps the most famous is the [classic Jupyter Notebook interface](https://jupyter-notebook.readthedocs.io/en/latest/), which allows the user to edit one file in each tab of their browser.

<!--picture-->

If you have a strong software engineering background, you may already have a preference for an Integrated Development Environment, or IDE. Popular IDE's like [VSCode](https://code.visualstudio.com/) and [PyCharm](https://www.jetbrains.com/pycharm/), which both have [decent features for developing](https://code.visualstudio.com/docs/datascience/jupyter-notebooks) notebooks. [ReviewNB](https://www.reviewnb.com/) has an excellent blog post about [choosing the right IDE](https://blog.reviewnb.com/choosing-the-right-ide/).

Finally, we want to talk about [JupyterLab](https://jupyterlab.readthedocs.io/en/latest/), which is is a more flexible interface for notebook development that allows users to click and drag more than one notebook or file side by side.

<!--picture-->

JupyterLab is sort of the best of both worlds when it comes to ease of entry and support for more advanced features. We believe that JupyterLab is a great choice for developers who are not already closely aquainted with a favorite IDE, but they are developing notebooks often enough to give the more advanced IDE-like features a try. 

Our [JupyterIDE](https://github.com/Accessible-Data-and-Code/jupyterlab-ide) repository was designed with this person in mind. JupyterIDE contains a list of useful extensions that can be easily installed to improve the development experience. The repository contains tutorials for how to use some of these extensions that provides useful features, for example, code completion. These tutorial were made with beginners in mind, and require no prior knowledge of IDE-like features, which is why we think developing notebooks in JupyterLab is a great stepping stone for developers who want to try out these features without having to how to learn an entirely new development environment.

### Reproducible Environments

Once you have picked a development environment, you may wonder what the best practices are for using Jupyter Notebooks in science and research contexts. It is important that notebooks used for research are computationally reproducible, meaning that, given all the files in your repository, an independent researcher could run your notebook without modification. This means that person reproducing your workflow doesn't have to guess which libraries you used to run the notebook. Ideally, your repository should have an environment or requirements file that makes it easy for the next person to download all the libraries they need to run your notebook. There are several choices for managing environments, but we recommend using [conda](https://docs.conda.io/en/latest/) to manage your environment. Check out [this post by Anaconda](https://www.anaconda.com/blog/8-levels-of-reproducibility) discusses various levels of reproducibility than can be achieved using conda.

### Sharing Notebooks

If you are looking to quickly share your notebook over the web for free, the [Binder](https://mybinder.org/) project, may be the easiest way to do so. Binder just requires that you provide a link to a GitHub repository containing a notebook and an environment file and it takes care of the rest! Binder makes it easy to share your interactive workflows with colleages.

### Creating Publications with Quarto

[Quarto](https://quarto.org/) is an open-source publishing platform authors can use to [turn notebooks into static output formats](https://quarto.org/docs/tools/jupyter-lab.html) such as HTML web pages and PDFs. Users can chose to include code blocks or graphical outputs produced by the code cell (like a graph), or both!

<!--picture-->

### Templates and Best Practices

Best practices are implemented in the [Notebook template repository](https://github.com/USRSE/jupyter-notebook-templates), which was created by the [United States Research Software Engineering Association](https://us-rse.org/) (US-RSE) for their inaugural conference in 2023.

### Jupyter Notebooks as Peer-Reviewed Objects

Speaking of conferences, notebooks are becoming an important part of scientific workflows. The academic system currently places high emphasis on peer-reviewed publications, but what if there was a way to bring these two important parts of the scientific process closer together to reduce researcher workload and improve better practices? There are many nascent efforts taking place on this front. The US-RSE conference [accepted Notebooks for peer-review]() starting in 2023. [American Geophysical Union](https://www.agu.org/) (AGU), through the Alfred P. Sloan funded effort [Notebooks Now!](https://agu-submission.curve.space/) are also spearheading efforts to standardize notebooks as a primary scholarly output formally included in peer review. There are also [electronic journals](https://www.journalovi.org/submit.html#experimental) popping up that accept Juptyer-notebook based submissions. Consider sharing your work with a broader audience by submitting to these venues! 


### Building Data Dashboards and Web Applications with Jupyter Notebooks

Another great way to share your research code and data to a broader audience is by creating a web application. For researchers, such a software development may feel combersome, but Jupyter Notebooks provides tool for rapidly developing simple, but highly interactice user interfaces. [Jupyter Widgets](https://github.com/jupyter-widgets/ipywidgets) allow users to add click and drag components to change variable values and interact with the visualizations in their workflows.

<!-- gif-->

In combination with a tool called [Voilà](https://github.com/voila-dashboards/voila), which hides the code cells in the notebook leaving only the widgets visible, developers familiar with Jupyter Notebooks can easily turn an interactive research workflow into a standalone data dashboard or web application. See the tutorial,
["How the Little Jupyter Notebook Became a Web App: Managing Increasing Complexity with nbdev"]({{< ref "/resources/scipy23" >}}).

### Conclusion

Jupyter4Science contains original content and curated resources about developing and sharing Jupyter Notebooks as they are used in the context of research. If you have resources to share or original content to propose, please visit [Contribute]({{< ref "/contribute" >}}) to learn more about how to get involved.
