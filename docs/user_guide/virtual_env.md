# Virtual environment <br />
Follow this step in order to work on your own virtual env locally (don't uploading libraries on Github !).<br />
What for ? Setting up a virtual environment when building a python project is an essential step in the development process. A virtual environment allows dependencies to be separated between projects. A dependency is just some sort of module that is required for your project to run properly. As the dependency modules are updated, conflicts can arise between projects if dependencies are shared and the necessary versions are not the same. A virtual environment eliminates these conflicts by allowing the dependencies to be project specific and isolated from the system. 

## Step to follow initialisation of virtual environment (venv) :
1) Run the script below within the directory to create your own virtual environment : 
```
python -m venv name_of_Venv
```
2) Activate your Venv, run next line :
```
cd name_of_Venv/Scripts
activate
```
3) You are now in the virtual environment, you can install the libraries required (cf requirements.txt).
For install libraries in EDF laptop, you need this next line (avoid restriction from admin) : 
```
pip install --trusted-host pypi.org --trusted-host files.pythonhosted.org -U name_library
```
4) Run ```deactivate``` to stop the virtual environment
5) Initialize the git repo by running ```git init```
6) Run the next line to include venv folder in the .gitignore files so the virtual environment is ignored in source control (will not be upload in remote repository) : 
```
echo name_of_Venv > .gitignore
```

## Work on the virtual environment [Visual Code version]: 
1) Activate your virtual environment : 
```
cd name_of_Venv/Scripts
activate
```
2) Change the select interpreter of visual code : 
[View> Command palette> Select interpreter> name_of_venv> Pyhon.exe]
3) Desactivate your venv :
```
cd name_of_Venv/Scripts
deactivate
```
## Update the list of libraries :
1) Install libraries you need in your venv : 
```
pip install --trusted-host pypi.org --trusted-host files.pythonhosted.org -U name_library
```
2) Update the requirements.txt, run the next line :
```
pip freeze > requirements.txt
```
3) Insure to add the file in source control : 
```
git add requirements.txt
```
4) You are able to commit your work (Don't forget to write a clair message for your commit !)