# AI/ML project template
This is the template for any ML project.
# Folder structure and Code Organisation
As much as you can organize your code in such as way it allow easy collaboration and usability. 
<details>
  <summary>Code organisation</summary>

## Code organisation
As much as you can organize your code in such as way it allow easy collaboration and usability. It is recommended to  organise the code based on the part of the pipeline you are creating such as (data, training, prediction, etc.). It consits the following folder structures.

```python

artefacts/
code/
dataset/
```

- **artefacts**        should have all the relevent artefacts of the project.
- **code**             should have all the relevent source-code of the project.
- **datasets**         should have all the datasets of the project here.


</details>

<details>
  <summary>Naming Convention</summary>

This post provide a detailed guideline on how to [structure and organise python code like a pro](https://guicommits.com/organize-python-code-like-a-pro/)
## Naming Convention

</details>

<details>
  <summary>Code documentation</summary>

## Documentation
Documentation provides the best way for organizing the code. It facilitates easy collaboration, code readability and usability.  As much as you could, it recommended to provide the following aspects as part of the documentation:
- Comments: Terse descriptions of why a piece of code exists.
- Typing: Specification of a function's inputs and outputs data types, providing insight into what a function consumes and produces at a glance.
```python
def sensor_data(seq: Sequence, max_seq_len: int = 0) -> np.ndarray:
    ...
    return data
```
- Docstrings: This is a meaningful description that describes the overall function or module and arguments, returns, etc.
>If you're using [Visual Studio Code](https://code.visualstudio.com/) (highly recommend), you should get the free Python Docstrings Generator extension so you can type """ under a function and then hit the Shift key to generate a template docstring. It will autofill parts of the docstring using the typing information and even exception in your code!

- Documentation: A rendered webpage that summarizes all the functions, classes, API calls, workflows, examples, etc., so we can view and traverse through the code base without actually having to look at the code just yet. You will create the documentation automatically from the codebase using the docstring provided.

</details>





# Packaging
It is advised to  create an environment explicitly detail all the requirements (python version, packages, etc.) for each project.
<details>
  <summary>Creating environment</summary>

## Packaging
There are many recommended options when it comes to packaging in Python such virtualenv or anaconda environment. 

To use virtualen you have to follow the following steps:
1. Installing virtualenv (Documentation https://virtualenv.pypa.io/en/stable/)

	`pip install virtualenv`
	
    OR

	`sudo apt install virtualenv`
2.  Create virtualenv with no libraries from your existing python installation

	`python3 -m venv imr_venv` or `virtualenv imr_venv` on windows computers.

3.  Active virtualenv

	`source imr_venv/bin/activate` or ``.\imr_venv\Scripts\activate`` or windows machine

4. Installing packages

	```pip install package_name4```.

5. Generate requirements.txt.  This gives the list of packages, and it’s version.

	`pip freeze > requirements.txt`

6. Install requirements from requirements.txt

	`pip install -r requirements.txt`


If you are interested on using conda environment 

1. Install [anaconda]() or [miniconda]()
2. Create  conda environment with specific python versions too. 

	```conda create -n imr_env python=3```
3. Activate conda environment
   ````conda activate mr_env``

4. Install packages
   ````conda install package_name````

5. Generate environment.yml.  This gives the list of packages, and it’s version.

	 ```conda env create -f environment.yml```

6. To list the package, we need to use the below command.

	````conda env list````


</details>

# Reproducibility
Versioning your project will ensure reproducible behavior.
<details>
  <summary>Versioning code</summary>


Versioning your project will ensure reproducible behavior. Versioning control is a fundamental tool in most software engineering. It tracks any change done to code, allowing the user to review the entire history of changes and possibly revert to an older version.

IMR uses [gitlab](https://about.gitlab.com/) withich a git cloud-based versioning services. For basic understanding of versionong commands and best practises we recommdend following this [tutorial](https://madewithml.com/courses/mlops/versioning/) and this [video talk](https://uniroma1.zoom.us/rec/play/4BEYvgGL1bpRL-MkiYXAov3Tz1GN-wSGeTVvPf7UynX4q4tUgQt1bZxN4ntwsJsiMibPPW1zs-Oseo79.txvOV6rsEWUTD4E-?startTime=1620371740000&_x_zm_rtaid=hRUVAhTGR_CmUB4ZpoGC9g.1622727125231.275d841bc3fd05ba570cd859a8587554&_x_zm_rhtaid=752)

Follow [this installation instruction](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) to install git environment in your computer.

After installation make sure yo set up use-mane and email.
````git config --global user.name "imr_user"````

````git config --global user.email imr_user@imr.ie ```` 

</details>

<details>
  <summary>Versioning artefacts</summary>

It is important to version the data and artfects associated with your project. We will use the [Data Version Control (DVC)](https://dvc.org/) library for it's simplicity, rich features and most importantly modularity.  DVC interact perfectly with Git.



 DVC has lots of other useful features (metrics, experiments, etc.) so be sure to explore those as well.
Versioning your project will ensure reproducible behavior.

To use DVC
1. Install  DVC
   
   ``pip install dvc``

   or download DVC version for your OS by following this [link](https://dvc.org/)

2. Initialize an existing Git repository.
    
     ``dvc init``

3. Establish where our remote storage will be. We be using the artefacts directory which won't be checked into our remote repository.
   
   ``dvc remote add -d storage artefacts``

4. Add files to be tracked by DVC. This will create text pointer files for each file
   

   ``dvc add artefacts/data/projects.json``

5. Push to remote storage
 
   ````dvc push````

For more details on how to use DVC you can follow this [tutorial](https://madewithml.com/courses/mlops/versioning/#add-data) and this [dvc exercise](https://github.com/sscardapane/reprodl2021/tree/exercise3_dvc)
</details>


# Creating Demo
At this stage, we need to create a data app/dashboard with an easy-to-use UI for your ML model function. The data app should easily integrate with the developed codebase. It should further allow sharing your key findings, results and demonstrator to all critical stakeholders without any technical with a certain level of interactivity. 

Several off-the-shelf and open-source platforms such as [Dash](https://plotly.com/dash/), [Gradio](https://gradio.app/), [Streamlit](https://streamlit.io/), [Panel](https://panel.holoviz.org/) etc for creating interactive and easy to use data apps exist. 



# Creating docker container of your project


