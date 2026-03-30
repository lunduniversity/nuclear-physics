
## Documentation for a JupyterLite Course Page for Neutron Lab in Nuclear Physics 

This page provides a browser-based notebook without any installation required.

<h2>Open the Notebook</h2>

<p><strong>Click below to open the browser-based notebook:</strong></p>

<p>
  <a href="https://lunduniversity.github.io/nuclear-physics/lab/index.html"><strong>Open the JupyterLite Notebook</strong></a>
</p>

<p>After opening the notebook, place your data files in the <code>neutron_data</code> folder.</p>






---

# 🚫 STAFF-ONLY INFORMATION BELOW

> [!CAUTION]
> Everything below this point is intended for employees and teaching assistants only.
> Students do not need the information below.

---

<details>
  <summary><strong>Click to expand staff-only documentation</strong></summary>
## How the course page works

The JupyterLite page allows students to open the course notebooks directly in a web browser. The course material is published as part of the deployed site, which makes the notebooks and supporting files available to all the students. (Deployment here means that after GitHub Actions builds the JupyterLite site, the result is uploaded to GitHub Pages and made available through the public notebook link - see below for more information on github actions and pages)

**Students are not able to see each other's files or solutions through the JupyterLite page.**

Files are stored locally in the student's own browser. Because of this, one student's work is not visible to another student on a different computer. The browser can keep files the student has opened or edited and parts of the JupyterLite environment, downloaded assets needed to run the page --> useful because it can make the site faster to reopen and may allow a student to continue working later in the same browser on the same device.

> [!IMPORTANT]
> The local storage mentioned above has limitations:  it is tied to the same browser on the same device and it may disappear if the browser data is cleared. **For that reason, students should download important notebooks regularly and not rely only on browser storage for long-term saving.**



### Template repository
The repository was created from the [jupyterlite/xeus-lite-demo](https://github.com/jupyterlite/xeus-lite-demo) template.

> [!WARNING]
> The original `.lib` folder was renamed to `python_files`, since `.lib` is included in `.gitignore`. I chose to keep it that way.


> [!NOTE]
> The setup is based on [**xeus**](https://github.com/jupyter-xeus/xeus),  a library for implementing Jupyter kernels. It manages much of the Jupyter Kernel Protocol, which allows developers to focus on the interpreter itself rather than the communication layer. Several Jupyter kernels are built on xeus, including **xeus-cling** for C++ and **xeus-python** for Python.
> For more background, see: [xeus-lite: Jupyter kernels in the browser](https://blog.jupyter.org/xeus-lite-379e96bb199d)




## Repository structure and file descriptions

<details>
  <summary>Click here for details!</summary>

  >



### 📦 How to install kernels and packages

You can install specific kernels and extra packages by adding them to the ``environment.yml`` file.

See https://jupyterlite-xeus.readthedocs.io/en/latest/environment.html for more documentation.

#### Example : JupyterLite with NumPy and Matplotlib

To create a JupyterLite deployment with NumPy and Matplotlib pre-installed, edit the ``environment.yml`` file as follows:

```yml
name: xeus-kernel
channels:
  - https://repo.prefix.dev/emscripten-forge-dev
  - https://repo.prefix.dev/conda-forge
dependencies:
  - xeus-python
  - numpy
  - scipy
  - matplotlib
  - ipywidgets
  - ipycanvas
  - ipympl
```


### `.github/build-environment.yml`
This file defines the environment used during the build process. It can be modified to add build-time dependencies, for example if extra JupyterLite plugins are needed.

### `.github/workflows/deploy.yml` 
This file defines the GitHub Actions workflow used to build the JupyterLite site and publish it to GitHub Pages whenever changes are pushed to the repository.

### `environment.yml` **Edit this file to add packages**
This file defines which kernels and packages should be available in the JupyterLite environment. These dependencies are installed during the build process and are then available to students in the browser.

### `jupyter_lite_config.json` **Edit this file to add extra folders to the built JupyterLite site**
This file defines how JupyterLite is built. In this repository, it specifies that the teaching material in the `content` folder should be included in the deployed site.

### `content/`
This folder contains the teaching material that will be included in the deployed JupyterLite site.


</details>



## Redeployment after changing build files

If you change any of the build-related files, such as:

- `.github/workflows/deploy.yml`
- `.github/build-environment.yml`
- `environment.yml`
- `jupyter_lite_config.json`

then GitHub Pages will not update instantly.

After you push your changes, GitHub Actions will start a new build and deployment process. This may take a few minutes before the updated JupyterLite page is available online.

You can follow the progress in the **Actions** tab on GitHub. There you can see whether the workflow is still running, has completed successfully, or has failed.

The screenshot below shows an example where the deployment is still in progress.

![Example of a GitHub Actions deployment in progress](docs/images/dep.PNG)


##  GitHub Actions and GitHub Pages

<details>
  <summary>Click here for details!</summary>

  >

### What is GitHub Actions?
**GitHub Actions** is GitHub's automation system. It can automatically run tasks whenever something happens in the repository (you do not have to do it manually through command e.g.), for example when changes are pushed to GitHub.
 GitHub Actions here are used to Build the JupyterLite site, prepare the final static website files and publish the result automatically.

### What is GitHub Pages?
**GitHub Pages** is GitHub's static website hosting service. It can publish a website directly from a GitHub repository.
GitHub Pages is used here to host the generated JupyterLite site so that students can open it through a normal web link.

</details>

## Repository structure 
```text
nuclear-physics/
├── .github/
│   ├── workflows/
│   │   └── deploy.yml
│   └── build-environment.yml
├── content/
│   ├── Neutron_data/    <---------------- Put your data files here after opening the notebook link above
│   ├── python_files/
│   └── NOTEBOOK_STUDENTS.ipynb
├── .gitignore
├── .nojekyll
├── README.md
├── environment.yml
└── jupyter_lite_config.json

```

</details>





--------------------------------------------------------------------------

