# Geany configuration
How I configure Geany to use with python inside a conda environment.

Taken from <https://stackoverflow.com/questions/42013705/using-geany-with-python-virtual-environment>


## Install xterm
Install `xterm` if it is not already installed.

There is this:

```
xterm -e "/bin/sh %c"
```
in *Preferences* => *Tools* => *Terminal*.


## Find python version and path
In your terminal.
Activate the environment `ENV` you want to use.

```
conda activate ENV
```

check which python is used.

```
python --version --version
```

Which gives something like: `Version X.Y.Z`.

Now find the `PATH` of the Python interpreter:

```which pythonX.Y``` for Linux and Mac 

```where pythonX.Y``` for Windows

Which should give something like:

```/home/User/anaconda3/envs/ENV/bin/pythonX.Y```

This is the Python interpreter `PATH`.


## Configure Geany for Project Sessions
Verify whether Geany is configured for Project Sessions. *Edit* => *Preferences* => *General* => *Miscellaneous*.
 
In the *Projects* section, tick both *Use project-based session files* and *Store project file inside the project-based directory*.
 
I am not sure that *Store project file inside the project-based directory* is really necessary.

 
## Conda/Anaconda environments
To configure the build commands for a project to use the interpreter of the environment:

In *Build* => *Set Build Commands*, at the *Execute Commands* modify *Execute* with:

```
/home/User/anaconda3/envs/ENV/bin/pythonX.Y "%f"
```

where `ENV` `X` `Y` are those found in **Find python version and path**. 


## Test
Test if everything was properly done. In Geany, save a python file with the following:

```python
import sys
print(sys.version)
```

and execute it (`F5`).

The output should be the same as found in **Find python version and path**.
