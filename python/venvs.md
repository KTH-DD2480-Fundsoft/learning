# Virtual Environments

One practice that is avoided in software engineering are *global dependencies*. These are dependencies that are installed on a global level on the system and thus will be used across all projects. The problems with this are many, one being dependency conflicts. Therefore, most sophisticated programming environments that are established for programming languages have some way of isolating the dependencies of projects so that these problems don't occur. 

The way Python do this is with so-called **virtual environments**

## Create a virtual environment and activate it

Navigate to the directory where you want to create you Python project and then run the following where `python` is the command you use to run Python. For many, the command isn't just `python` as you probably know since that might point to the Python2 embedded version of the OS. Anyhow:

```
python -m venv .venv
```

What this command does is creating a virtual environment with the command `python -m venv` with the name `.venv`. This is a pretty standard name for a virtual environment. We make it hidden because we don't want to touch the files of the virutal environment. We only need to activate it. To do so we need to navigate to the corresponding activate file that will work for our system. For UNIX systems it will be located at `.venv/bin/activate`. So we run:

```
. .venv/bin/activate
```

We should have a "`(.venv)`" prefixed on our terminal prompt, indicating that the virtual environment is activated. To deactivate it, simply run:

```
deactivate
```

## Using the virtual environment

So now that the virtual environment is activated, whenever you run `python` or `pip`, your shell will run the executables provided by the virutal environment. So whenever you install something with `pip`, it won't install packages globally. Instead it will only install wihtin the virutal environment. In any moment, you can safely delete the `.venv` folder and all the installed packages that are contained wihtin it. Thus, this folder must not be committed and therefore must be gitignored (*i.e., added to the `.gitignore` file*).