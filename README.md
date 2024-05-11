# Data Version Control

## Task Description
<p align="justify">The practice involves setting up and storing data using DVC on GitHub. The aim is to observe how DVC streamlines data management, enhancing reproducibility, and scalability in machine learning workflows. In this context, DVC (Data Version Control) is a tool utilized for versioning and tracking changes in data. DVC collaborates with Git to efficiently manage data versions, keeping data separate from source code, and enabling seamless collaboration among teams.</p>

### Requirements

Before doing a DVC practicum in this MLOps course, make sure you have installed the following required requirements:

1. **Python:**
    - For Windows OS
        ```
        python --version 
        ```
        
    - For Linux, MacOS, etc
        ```
        python3 --version 
        ```
    > Note: If Python is not installed, download it here [Download Python](https://www.python.org/downloads/).

2. **Git:**
    ```
    git --version 
    ```
    > Note: If Git is not installed, download it here [Download Git](https://git-scm.com/downloads).

3. **DVC:**
  	```
    dvc --version 
    ```
  	> Note: If DVC is not installed, install it using the `pip install dvc` command in the terminal.

### Tutorial
Follow the tutorial below for Windows

1. **Open Terminal or Windows PowerShell.**

2. **Set Global User Configuration for Git:**
    ```
    git config --global user.name "yourname"
    git config --global user.email "youremail@gmail.com"
    ```

3. **Create Virtual Environment:**
    ```
    python -m venv venv-dvc
    ```

4. **Activate the Virtual Environment:**
    - For Windows OS
      ```
      venv-dvc\Scripts\activate
      ```
      
    - For Linux, MacOS, etc
      ```
      source venv-dvc/bin/activate
      ```
5. **Install DVC on the Virtual Environment that has been created**
     ```
     pip install dvc
     ```

6. **Initialize a Project**

    - Initialize a Git repository.
      ```
      git init
      ```

    - Initialize DVC inside the Git project.
      ```
      dvc init
      ```

    - A few internal files are created that should be added to Git:.
      ```
      git status
      ```

    - Commit DVC initialization.
      ```
      git commit -m "Initialize DVC"
      ```

7. **Tracking Data**

    - Create a data folder inside our project directory.
      ```
      mkdir data
      ```

    - Download sample data from Dataset Registry.
      ```
      dvc get https://github.com/iterative/dataset-registry get-started/data.xml -o data/data.xml
      ```

    - Add data to DVC tracking.
      ```
      dvc add data/data.xml
      ```

    - Add "data.xml.dvc" and ".gitignore" to Git repository.
      ```
      git add "data\data.xml.dvc" "data\.gitignore"
      git commit -m "Add raw data"
      ```

    - View the contents of the data folder.
      ```
      ls data
      ```

    - To view the contents of the `data.xml.dvc` file with the `cat` command:
      ```
      cat data.xml.dvc
      ```

    - Double the size of the data owned.
      ```
      copy data/data.xml tmp/data.xml
      cat tmp/data.xml >> data/data.xml
      ```
      > Note: If there is no `tmp` folder yet, create a `tmp` folder using the 'mkdir tmp' command.

    - View Git log in oneline format.
      ```
      git log --oneline
      ```

    - Revert to the previous data version.
      ```
      git checkout HEAD^1 data/data.xml.dvc
      dvc checkout
      ls data
      git commit data/data.xml.dvc -m “Revert dataset updates”
      ```
      > Note: Use `dvc checkout` to ensure your data files match the state they were in at the previous commit. `ls data` to see the data, whether it is the same size as the original

8. **Git Remote Repository**

    - Create a new repository on GitHub.
      ![image](https://github.com/johannawawi/DVC_Basics/assets/145430844/a923f792-aaeb-4882-bc76-450e68184894)

    - Push the local repository to the Git repository.
      ```
      git remote add origin https://github.com/johannawawi/DVC_Basics.git
      git branch -M main
      git push -u origin main
      ```

9. **Now try using a local dataset that you have**
   
    Follow the above tutorial well. For example here I use `electrial_grid.csv` data that I saved in the `mydata` folder.
