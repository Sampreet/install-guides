# Python Environment inside Visual Studio Code

> A guide for setting up the Python environment inside Visual Studio Code.

## Installation

### Python via Anaconda/Miniconda Distribution

[![Conda](https://img.shields.io/conda/v/conda-forge/python?style=flat-square)](https://github.com/python/cpython)
![Conda](https://img.shields.io/conda/dn/conda-forge/python?style=flat-square)

*Python* is an interpreted, high-level, general-purpose language supporting object-oriented programming with more emphasis on code-readibility and extensibility. A complete guide to install and configure Python via Anaconda/Miniconda Distribution can be found in [this link](https://github.com/Sampreet/install-guides/blob/master/languages/python/python-anaconda-miniconda.md).

### Visual Studio Code

[![GitHub package.json version](https://img.shields.io/github/package-json/v/Microsoft/vscode?style=flat-square)](https://github.com/microsoft/vscode)
![GitHub](https://img.shields.io/github/license/Microsoft/vscode?style=flat-square)

*Visual Studio Code* (VSCode) is an open-source, highly-customizable and versatile source-code editor developed by Microsoft which supports debugging, version control, syntax highlighting, intelligent code completion, snippets, and code refactoring. Download the appropriate setup file for your operating system (Windows/Linux/MacOSX) from the [official page](https://code.visualstudio.com/download) and install. Easy!

### Microsoft's Python Extension

[![GitHub package.json version](https://img.shields.io/github/package-json/v/Microsoft/vscode-python?style=flat-square)](https://github.com/microsoft/vscode)
![GitHub](https://img.shields.io/github/license/Microsoft/vscode-python?style=flat-square)

*Python* extension for VSCode by Microsoft provides a rich support for the language including a whole bundle of features for easy execution of Python scripts. Install the latest version of this extension from VSCode's Marketplace, the last icon on VSCode's *activity bar* (left edge). It usaully stays at the top with nearly 20M downloads:

![Python Extension](https://raw.githubusercontent.com/Sampreet/install-guides/master/editors/screenshots/vscode-python-marketplace.png)

Once the installation is complete, reload VSCode for the changes to take effect.

## Testing

Open any folder containing Python scripts.

Alternatively, create a ```.py``` file (say, ```helloworld.py```) inside VSCode and add the following line:

```python
print("Hello World!")
```

Save the file inside a folder (say, ```test```). Now, on the file explorer on VSCode's *side bar* (second-from-left panel), click on the ```.py``` file. The Python extension will load automatically.

### Selecting the Python Environment

Whenever any ```.py``` file is selected, VSCode's Python extension loads automatically. Select the corresponding ```conda``` environment by clicking on the text mentioning the current ```python``` interpreter at the bottom left corner of the VSCode window:

![Python Environment](https://raw.githubusercontent.com/Sampreet/install-guides/master/editors/screenshots/vscode-python-env.png)

### Running Python Files

Right click the ```.py``` file in the VSCode file explorer to open the context menu. Select ```Run Python File in Terminal```. This will open a new terminal inside VSCode, activate the selected Python environment and execute the file there:

![Python File Execution](https://raw.githubusercontent.com/Sampreet/install-guides/master/editors/screenshots/vscode-python-file-exec.png)

### Opening IPython/Jupyter Notebooks

Create a IPython/Jupyter Notebook file (say, ```notebook.ipynb```) and click on the ```.ipynb``` file in the VSCode file explorer. The Jupyter server will load automatically with all the options to insert/run cells, stop/restart kernel, etc displayed on a top panel. Markdown and Python scripts can be toggled by using the ```M↓``` and ```{}``` options on top of each cell. Hit ```Shift+Enter``` to execute a cell. Python outputs are displayed below the cell upon execution:

![Jupyter Notebook](https://raw.githubusercontent.com/Sampreet/install-guides/master/editors/screenshots/vscode-python-jupyter-nb.png)
