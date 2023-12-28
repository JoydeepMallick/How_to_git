# ✅Uploading Files to GitHub Using Git Command Line

## Introduction

This guide provides a step-by-step of using Git CLI to manipulate github.
The 👁😦 answer of stackoverflow :- [👀👀👀](https://stackoverflow.com/questions/65924087/github-problem-git-pushes-to-master-branch-not-main-and-cant-merge-the-two)

## Prerequisites

- [Git](https://git-scm.com/) installed on your machine.
- A GitHub account.

## Steps

1. <h3>Create a new repository via github CLI</h3>

   Using `curl` command we can access our github profile and then create a new repository, in order to access github account we need **Personal Access Tokens** for our github.
   [Read more](https://docs.github.com/en/rest/repos/repos?apiVersion=2022-11-28#create-a-repository-for-the-authenticated-user)
   ```bash
   curl -u YourGithubUsername:YOUR_TOKEN https://api.github.com/user/repos -d '{"name":"YourRepositoryName"}'
   ```
   **🔥NOTE🔥** : `curl` command works fine in windows via `wsl`(✔Checked and Verified), powershell does support curl but it has some weird behavior and command prompt does not have curl but curl can be seperately installed in system or via git bash terminal also its possible.
   
   <h4>How to generate personal access tokens in github</h4>
   
      To obtain a personal access token on GitHub, follow these steps:

      i. **Visit GitHub:**
         Open your web browser and go to GitHub.

      ii. **Sign In:**
          If you're not already signed in, sign in to your GitHub account.

      iii. **Go to Settings:**
          Click on your profile picture in the top right corner of the page, and from the dropdown menu, select "Settings."

      iv. **Navigate to Developer Settings:**
          In the left sidebar, click on "Developer settings."

      v. **Create a Personal Access Token:**
           Click on "Personal access tokens" in the left sidebar.
           Click the **"Generate token"** button.

      vi. **Configure the Token:**
           Enter a name for your token.
           Select the desired scopes for your token. For creating repositories, you'll need at least the `"repo"` scope.
           Click the "Generate token" button.

      vii. **Copy the Token:**
          After generating the token, copy it immediately. This is the only time GitHub will display the token, so make sure to store it securely.
   

      Once you have the token, you can use it for authentication when making requests to the GitHub API for the limited time you keep it active, as demonstrated in the curl command example.

2. #### **Navigate to the Project Folder:**

   Open the command prompt or terminal and navigate to the desired project folder using the `cd` command:

   ```bash
   cd path/to/your/project
   ```

3. #### **Initialize Git Repository:**

   Run the following command to initialize a Git repository in the project folder. It creates a `.git` folder in pwd:

   ```bash
   git init
   ```

4. #### **Add Files to Local Repository:**

   Add files to the local repository using the git add command. You can either specify individual file names or use a space-separated list to add multiple files and folders.

   ```bash
   git add <filename1> <filename2> <foldername1> <foldername2>
   ```

   **Or** to add all files:

   ```bash
   git add .
   ```

5. #### **Commit the added files with a descriptive message:**

   Commit the changes to the local git repository initialised in present working directory.

   ```bash
   git commit -m "Your commit message here"
   ```

6. #### **Add Remote Repository:**

   Add the GitHub repository as a remote location. Replace _`GitHubUsername`_ and _`RepoName`_ with **your GitHub username** and **repository name**.

   ```bash
   git remote add github https://github.com/GitHubUsername/RepoName.git
   ```

   #### ⚠ NOTE :-

   If you **need to update the remote URL later, you can use the following command instead** of `git remote add ....` which can be used only once ❗👀:

   ```bash
   git remote set-url github https://github.com/NewOrSameGitHubUsername/NewOrSameRepoName.git
   ```

7. #### **Push Changes to GitHub Repository:**

   Push the committed changes to the GitHub repository. Replace `BranchName` with the branch you want to push (e.g., **master** or **main** or any other).

   ```bash
   git push -u github BranchName
   ```

   Use the `-u flag` for the **first push to set the upstream branch**.

   If you encounter issues, **you can force the push with the `-f flag`:**

   ```bash
   git push -f github BranchName
   ```

8. It **might ask permission to use your github or ask you to sign in once on the screen for permissions** and then when all done, check the repo, its updated with all the commit messages you wrote.



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

1. https://www.varonis.com/blog/how-to-merge-in-git
2. https://stackoverflow.com/questions/10904339/github-fatal-remote-origin-already-exists
3. https://www.youtube.com/watch?v=H4mp_aYK5bA
4. Merging problems - https://stackoverflow.com/questions/68460171/how-to-merge-master-branch-into-main
5. Merging problems - https://www.educative.io/answers/the-fatal-refusing-to-merge-unrelated-histories-git-error

Youtube video coming soon, [click me!](./do_not_open/about_to_meet_god_soon.gif)
