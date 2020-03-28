# LaTeX Environment inside Visual Studio Code

> A guide for setting up the LaTeX environment inside Visual Studio Code.

## Installation on Windows/Linux/MacOSX

### Visual Studio Code

[![GitHub package.json version](https://img.shields.io/github/package-json/v/Microsoft/vscode?style=flat-square)](https://github.com/microsoft/vscode)
![GitHub](https://img.shields.io/github/license/Microsoft/vscode?style=flat-square)

*Visual Studio Code* (VSCode) is an open-source, highly-customizable and versatile source-code editor developed by Microsoft which supports debugging, version control, syntax highlighting, intelligent code completion, snippets, and code refactoring. Download the appropriate setup file for your operating system (Windows/Linux/MacOSX) from the [official page](https://code.visualstudio.com/download) and install. That's it!

### LaTeX Workshop 

[![GitHub package.json version](https://img.shields.io/github/package-json/v/James-Yu/LaTeX-Workshop?style=flat-square)](https://github.com/James-Yu/LaTeX-Workshop)
![Visual Studio Marketplace Downloads](https://img.shields.io/visual-studio-marketplace/i/James-Yu.latex-workshop?style=flat-square)
![GitHub](https://img.shields.io/github/license/James-Yu/LaTeX-Workshop?style=flat-square)

*LaTeX Workshop* by James Yu is VSCode's most popular extension for LaTeX which provides the core features for LaTeX typesetting inside VSCode. 

#### Installing the Dependencies

##### MiKTeX

*MiKTeX* is a free latex typesetting system providing all tools required by LaTeX Workshop for compiling ```.tex``` files. Download the setup for your OS (Windows/Mac/Linux/Docker) from the [official downloads page](https://miktex.org/download) and install.

##### Perl

*Perl* is a high-level programming language required by LaTeX Workshop's ```pdflatex``` for the creation of ```.pdf``` files. [Get Perl](https://www.perl.org/get.html) for your operating system and install.

#### Installing the Extension

Install the latest version of the extension LaTeX Workshop from VSCode's Marketplace, the last icon on VSCode's *activity bar* (left edge). It usaully stays at the top with 500K+ downloads:

![LaTeX Workshop Extension](https://raw.githubusercontent.com/Sampreet/install-guides/master/editors/screenshots/vscode-latex-marketplace.png)

Once the installation is complete, reload VSCode for the changes to take effect.

## Testing

Open any folder containing a LaTeX project.

Alternatively, create a ```.tex``` file (say, ```main.tex```) inside VSCode and add the following lines:

```latex
\documentclass[11pt, a4paper]{article}
\usepackage{amsmath}
\begin{document}
\centering 
    Hello World!
\end{document}
```

Save the file inside a folder (say, ```test```). Now, on the file explorer on VSCode's *side bar* (second-from-left panel), click on the ```.tex``` file. A new icon resembling ```TEX``` will appear below the marketplace icon in the *activity bar*:

![LaTeX Workshop Icon](https://raw.githubusercontent.com/Sampreet/install-guides/master/editors/screenshots/vscode-latex-tex.png)

Click the icon, and select the ```Build LaTeX project``` command:

![LaTeX Workshop Commands](https://raw.githubusercontent.com/Sampreet/install-guides/master/editors/screenshots/vscode-latex-commands.png)

This will compile the ```.tex``` file and create the ```.pdf``` file by the same name inside the folder. Select the ```View LaTeX PDF``` command to view the output file in your window of choice (VSCode tab/web browser/external viewer). Here's a screenshot of the ```.tex``` file (left tab) and the ```.pdf``` file (zoomed) displayed in a VSCode tab (right):

![LaTeX Workshop Commands](https://raw.githubusercontent.com/Sampreet/install-guides/master/editors/screenshots/vscode-latex-window.png)


