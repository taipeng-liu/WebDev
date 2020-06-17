This post provides several ways you can write and run code in Python. 

## Online Notebook
You may run and store your Python code in a `.iphnb` file remotely. Following is a list of online free notebooks:

* [Kaggle](www.kaggle.com)
* Google [Colab](colab.research.google.com)
* Microsoft [Azure](notebooks.azure.com)

## Local Notebook
* [Jupyter Notebook](jupyter.org/install) <br>
    If you have installed `pip`, you can type in this command to install it in terminal:
    ```
    pip install notebook
    ``` 
    and run it using:
    ```
    jupyter notebook
    ```
    

## Terminal

If you are running Linux and prefer to run Python in terminal.

First, install Python dependencies:

```
sudo apt-get update
sudo apt-get install --no-install-recommends make build-essential libssl-dev zlib1g-dev libbz2-dev libreadline-dev libsqlite3-dev wget curl llvm libncurses5-dev xz-utils tk-dev libxml2-dev libxmlsec1-dev libffi-dev liblzma-dev
```

Then, install Python:

```
sudo apt-get install python
```

Now you can run `python` directly, or add your `.py` program as argument to run:

```
python [example.py]
```

If you have `pip` installed, you can use it to install Python packages such as `numpy` and `pandas`:

```
pip install numpy
pip install pandas
```

(Optional) I also recommend you to install pyenv to manage your Python version. This tool is useful when you want to apply different versions of Python while keeping your original version and setups. Please follow the instructions [here](github.com/pyenv/pyenv) to install it.

You can check the installation of pyenv by typing in:
```
pyenv versions
```
Install another version of Python (e.g., 3.7.0):
```
pyenv install 3.7.0
```
and use the version:
```
pyenv global 3.7.0
```
Uninstall it:
```
pyenv uninstall 3.7.0
```