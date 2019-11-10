# Pipenv Cheatsheets 

## Pipenv

**GENERAL**

`pip install pipenv` to install Pipenv

`pipenv install requests` to create a virtualenv and install the requests package. It will also create two files, *Pipfile* and *Pipfile.lock* 

`pipenv install -r ../snippets/requirements.txt` to install multiple dependancies for your project. You will use your own location of file requirements.txt. It will update Pipfile and Pipfile.lock 

`pipenv install pytest --dev` will install the package to dev, will not be shipped with production code. 

`pipenv lock -r`  is the equivilent of `pip freeze` 

`pipenv graph` will show the installed packages and the dependencies for this package. 

`pipenv uninstall requests` to uninstall requests package

`pipenv shell` to activate the virtualenv 

`exit` to deactivate the virtualenv

`pipenv run` to run a command inside the virtualenv

`pipenv run python` when you are in your project folder. You could also run script, `pipenv run python script.py`

`pipenv --venv` will give you the path of your virtual environmens 

*TOML* format is being used in the Pipfile. Pipfile is meant to be editable. 

Use the code below to find out which python you are using: 
``` Python
import sys
sys.executable
```

`pipenv check` 

**USE A DIFFERENT VERSION OF PYTHON** 

1. Change the version of python in the Pipfile
2. Recreate python virtual environment. `pipenv --python 3.6` the version that you specified in the Pipfile. 

**ALTERNATIVE WAY FOR USING DIFFERENT VERSION OF PYTHON** 

Remove the environment completely, then recreate from scratch using Pipfile

1. `pipenv --rm` to remove an virtual environment completly. Only removes the environments, but everything we need to create the environment is in the Pipfile. 
2. `pipenv install` do not put any options. 

**UPDATE DIFFERENT VERSION OF A PACKAGE**

1. Update the package version in Pipfile
2. `pipenv install` do not put any options. 

**READY TO PUT YOUR CODE IN PRODUCTION**

1. Create or update the Pipfile.lock with current depandencies `pipenv lock` 
2. `pipenv install --ignore-pipfile` to install depandencies from Pipfile.lock for the exact version of packages that being used in your development. 

**SET ENVIRONMENT VARIABLES**
1. Create `.env` file within your project directory. You can send environment variable in this file or multiple environment variables in this file. 

```Python
SECRETE_KEY="MysuperSecretKey"

```
if you run `pipenv run python` you will see **Loading .env environment variables** displayed before the Python version. 
To use the environment variable in Python: 

```Python
import os
os.environ['SECRET_KEY] # when you run this code, you will see the value that you assigned to this variable. 

```
**Do NOT commit .env files to your repository, you might want add .env to your ignore file** 

















 