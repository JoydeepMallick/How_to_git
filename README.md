# ✅Uploading Files to GitHub Using Git Command Line

## Introduction

This guide provides a step-by-step process to upload files from the command line using Git and push them to a GitHub repository.

## Prerequisites

- [Git](https://git-scm.com/) installed on your machine.
- A GitHub account.

## Steps

1. #### **Navigate to the Project Folder:**

   Open the command prompt or terminal and navigate to the desired project folder using the `cd` command:

   ```bash
   cd path/to/your/project
   ```

2. #### **Initialize Git Repository:**

   Run the following command to initialize a Git repository in the project folder. It creates a `.git` folder in pwd:

   ```bash
   git init
   ```

3. #### **Add Files to Local Repository:**

   Add files to the local repository using the git add command. You can either specify individual file names or use a space-separated list to add multiple files and folders.

   ```bash
   git add <filename1> <filename2> <foldername1> <foldername2>
   ```

   **Or** to add all files:

   ```bash
   git add .
   ```

4. #### **Commit the added files with a descriptive message:**

   Commit the changes to the local git repository initialised in present working directory.

   ```bash
   git commit -m "Your commit message here"
   ```

5. #### **Add Remote Repository:**

   Add the GitHub repository as a remote location. Replace _`GitHubUsername`_ and _`RepoName`_ with **your GitHub username** and **repository name**.

   ```bash
   git remote add github https://github.com/GitHubUsername/RepoName.git
   ```

   #### ⚠ NOTE :-

   If you **need to update the remote URL later, you can use the following command instead** of `git remote add ....` which can be used only once ❗👀:

   ```bash
   git remote set-url github https://github.com/NewOrSameGitHubUsername/NewOrSameRepoName.git
   ```

6. #### **Push Changes to GitHub Repository:**

   Push the committed changes to the GitHub repository. Replace `BranchName` with the branch you want to push (e.g., **master** or **main** or any other).

   ```bash
   git push -u github BranchName
   ```

   Use the `-u flag` for the **first push to set the upstream branch**.

   If you encounter issues, **you can force the push with the `-f flag`:**

   ```bash
   git push -f github BranchName
   ```

7. It **might ask permission to use your github or ask you to sign in once on the screen for permissions** and then when all done, check the repo, its updated with all the commit messages you wrote.

# ⚠Moving Files to a Specific Folder in GitHub Repository

## Scenario

Suppose you have added a file named `A.cpp` to your local repository without specifying its location. Now you want to move it to the `code/cppcodes/` folder in the remote repository named `HelloGit`.

The below steps explain such a scenario from beginning.

## Steps

1. #### **Navigate to the file location within Project Folder:**

   Open the command prompt or terminal and navigate to the desired project folder using the `cd` command:

   ```bash
   cd path/to/your/filelocation/
   ```

2. #### **Initialize Git Repository:**

   Run the following command to initialize a Git repository in the current folder. It creates a `.git` folder in pwd:

   ```bash
   git init
   ```

3. #### **Add the File Randomly:**

   Add the file to the local repository :

   ```bash
   git add A.cpp
   ```

4. #### **Commit the Changes:**

   Commit the staged changes in locat git repository with a descriptive message:

   ```bash
   git commit -m "Add A.cpp randomly"
   ```

5. #### **Add Remote Repository:**

   Add the GitHub repository as a remote location. Replace `GitHubUsername` with **your GitHub username**.

   ```bash
   git remote add github https://github.com/GitHubUsername/HelloGit.git
   ```

6. #### **Push Changes to GitHub Repository at desired location:**

   Push the committed changes to the GitHub repository. Replace `BranchName` with the branch you want to push (e.g., **master** or **main** or any other) then colon(`:`) and then location.

   ```bash
   git push -f github BranchName : code/cppcodes
   ```

## ⚠After step 3 we could have also done the below steps:-

4. #### **Move the file to required directory**

   If the directory does not exist, first create it in locally then use git-mv to moves files in required directory following the format `git-mv <sourcefile_or_directory> <destination_directory>`.

   ```bash
   git-mv A.cpp code/cppcodes/
   ```

5. #### **Commit the changes to local repository:**

   ```bash
   git commit -m "Move A.cpp to code/cppcodes/"
   ```

6. #### **Add Remote Repository:**

   Add the GitHub repository as a remote location. Replace `GitHubUsername` with **your GitHub username**.

   ```bash
   git remote add github https://github.com/GitHubUsername/HelloGit.git
   ```

7. #### Push the changes to Remote repository

   ```bash
   git push -f github BranchName
   ```


# Overriding main branch with master branch👀
   
   ```bash
   git push -f github master:main
   ```
   
   **Purpose:** Forcefully pushes your local master branch to the remote main branch.
   
   **Explanation:** This command **overwrites the remote main branch with your local master branch history, potentially discarding any changes that existed on the remote branch but not in your local branch**. Use it with caution, as it can lead to data loss if not coordinated with collaborators.
   
```bash
git init                                                          <-------- initializing in master branch
git add .                                                         <-------- Stages all files in the current directory and its subdirectories for commit.
git commit -m "commited"                                          <-------- Commits the staged changes with a descriptive message
git remote add github https://github.com/userName/repoName.git    <-------- Connects your local repository to a remote repository on GitHub.
git fetch github main                                             <-------- Fetches the latest changes from the remote main branch.
git push -f github master:main                                    <-------- Forcefully pushes your local master branch to the remote main branch.
```
### 👀👀👀

Helpful resources :-

1. https://stackoverflow.com/questions/10904339/github-fatal-remote-origin-already-exists
2. https://www.youtube.com/watch?v=H4mp_aYK5bA
3. Merging problems - https://stackoverflow.com/questions/68460171/how-to-merge-master-branch-into-main
4. Merging problems - https://www.educative.io/answers/the-fatal-refusing-to-merge-unrelated-histories-git-error

Youtube video coming soon, [click me!](./do_not_open/about_to_meet_god_soon.gif)
