### Introduction

In this lesson, we'll cover common Git commands used to manage your projects and to upload your work onto GitHub. We refer to these commands as the **basic Git workflow**. When you're using Git, these are the commands that you'll use 70-80% of the time. So if you can get these down, you'll be more than halfway done mastering Git!

### Lesson Overview

This section contains a general overview of topics that you will learn in this lesson.

 -   How to create a repository on GitHub
 -   How to get files to and from GitHub
 -   How to take "snapshots" of your code

### Assignment

<div class="lesson-content__panel" markdown="1">

#### Before you start!

-   Github recently updated the way it names the default branch. This means you need to make sure you are using a recent version of git (2.28 or later). You can check your version by running:
`git --version`
-   If you haven't already, set your <span id="main-push"></span>local default git branch to `main`. You can do so by running:
`git config --global init.defaultBranch main`
-   For more information on the change from `master` to `main` see [GitHub's Renaming Repository](https://github.com/github/renaming).

#### Create the Repository

1.  <span id="new-github-repo"></span>You should have already created a GitHub account in the [Setting Up Git](https://www.theodinproject.com/lessons/foundations-setting-up-git) lesson. If you haven't done that yet, you can sign up [here](https://github.com/).

2.  Create a new repository by clicking the button shown in the screenshot below.

    ![The GitHub Profile Screen](https://cdn.statically.io/gh/TheOdinProject/curriculum/b54d14c5dcee1c6fac61aee02fca7e9ef7ba1510/foundations/git_basics/project_practicing_git_basics/imgs/00.png)

3.  Give your repository the name "git_test" in the repository name input field. Check "Add a README file". And then create the repository by clicking the green "Create repository" button at the bottom of the page.

   ![Create new repo using GitHub](https://cdn.statically.io/gh/TheOdinProject/curriculum/b54d14c5dcee1c6fac61aee02fca7e9ef7ba1510/foundations/git_basics/project_practicing_git_basics/imgs/01.png)

4.  This will redirect you to your new repository on GitHub. To get ready to copy (clone) this repository onto your local machine, click the green "Code" button. Then select the SSH option, and copy the line below it. **NOTE: You MUST click the SSH option to get the correct URL.**

   ![Copy SSH link using GitHub](https://cdn.statically.io/gh/TheOdinProject/curriculum/b54d14c5dcee1c6fac61aee02fca7e9ef7ba1510/foundations/git_basics/project_practicing_git_basics/imgs/02.png)

5.  Let's use the command line on your local machine to create a new directory for all of your Odin projects. Create a directory called `repos` with the `mkdir` command in your home folder. If you're not sure if you're in your home folder, just type `cd ~`. Once it's made, move into it with the `cd` command.

   ![Creating a new directory](https://cdn.statically.io/gh/TheOdinProject/curriculum/b54d14c5dcee1c6fac61aee02fca7e9ef7ba1510/foundations/git_basics/project_practicing_git_basics/imgs/03.png)

6.  <span id="github-to-local"></span>Now it's time to clone your repository from GitHub onto your computer with `git clone` followed by the URL you copied in the last step. The full command should look similar to `git clone git@github.com:USER-NAME/REPOSITORY-NAME.git`. If your URL looks like `https://github.com/USER-NAME/REPOSITORY-NAME.git`, you have selected the HTTPS option, not the required SSH option.

    ![Clone the repo using CLI](https://cdn.statically.io/gh/TheOdinProject/curriculum/b54d14c5dcee1c6fac61aee02fca7e9ef7ba1510/foundations/git_basics/project_practicing_git_basics/imgs/04.png)

7.  <span id="origin-push"></span>That's it! You have successfully connected the repository you created on GitHub to your local machine. To test this, you can `cd` into the new **git_test** folder that was downloaded and then enter `git remote -v` on your command line. This will display the URL of the repository you created on GitHub, which is the remote for your local copy. <span id="default-remote"></span>You may have also noticed the word **origin** at the start of the `git remote -v` output, which is the name of your remote connection. The name "origin" is both the default and the convention for the remote repository. But it could have just as easily been named "party-parrot" or "dancing-banana". (Don't worry about the details of origin for now; it will come up again near the end of this tutorial.)

    ![Check repo remotes using CLI](https://cdn.statically.io/gh/TheOdinProject/curriculum/b54d14c5dcee1c6fac61aee02fca7e9ef7ba1510/foundations/git_basics/project_practicing_git_basics/imgs/05.png)

#### Use the Git Workflow

1.  Create a new file in the `git_test` folder called "hello_world.txt" with the command `touch hello_world.txt`.

    ![Create hello_world.txt using CLI](https://cdn.statically.io/gh/TheOdinProject/curriculum/b54d14c5dcee1c6fac61aee02fca7e9ef7ba1510/foundations/git_basics/project_practicing_git_basics/imgs/06.png)

2.  <span id="git-status"></span>Type `git status` in your terminal. In the output, notice that your hello_world.txt file is shown in red, which means that this file is not staged.

    ![Check status of repo using CLI](https://cdn.statically.io/gh/TheOdinProject/curriculum/b54d14c5dcee1c6fac61aee02fca7e9ef7ba1510/foundations/git_basics/project_practicing_git_basics/imgs/07.png)

3.  <span id="git-add"></span><span id="two-stages"></span>Type `git add hello_world.txt`. This command adds your hello_world.txt file to the staging area in Git. The staging area is part of the two-step process for making a commit in Git. Think of the staging area as a "waiting room" for your changes until you commit them. Now, type `git status` again. In the output, notice that your file is now shown in green, which means that this file is now in the staging area.

    ![Stage hello_world and check repo status again using CLI](https://cdn.statically.io/gh/TheOdinProject/curriculum/b54d14c5dcee1c6fac61aee02fca7e9ef7ba1510/foundations/git_basics/project_practicing_git_basics/imgs/08.png)

4.  <span id="git-commit"></span>Type `git commit -m "Add hello_world.txt"` and then type `git status` once more. The output should now say: "*nothing to commit, working tree clean*", indicating your changes have been committed. Don't worry if you get a message that says "*upstream is gone*". This is normal and only shows when your cloned repository currently has no branches. It will be resolved once you have followed the rest of the steps in this project.

    The message, "*Your branch is ahead of 'origin/main' by 1 commit*" just means that you now have newer snapshots than what is on your remote repository. You will be uploading your snapshots further down in this lesson.

    ![Commit hello_world and check repo status again using CLI](https://cdn.statically.io/gh/TheOdinProject/curriculum/b54d14c5dcee1c6fac61aee02fca7e9ef7ba1510/foundations/git_basics/project_practicing_git_basics/imgs/09.png)

5.  <span id="git-log"></span>Type `git log` and look at the output. You should see an entry for your "*Add hello_world.txt*" commit. You will also see details on the author who made the commit and the date and time of when the commit was made. If your terminal is stuck in a screen with (END) at the bottom, just press "q" to escape. You can configure settings for this later, but don't worry about it too much for now.

    ![Commit hello_world and check repo status again using CLI](https://cdn.statically.io/gh/TheOdinProject/curriculum/b54d14c5dcee1c6fac61aee02fca7e9ef7ba1510/foundations/git_basics/project_practicing_git_basics/imgs/10.png)

#### Modify a file or two

1.  Open README.md in your text editor of choice. In this example, we will open the directory in Visual Studio Code by using the command `code .` inside your repository.

    ![Add text file and check repo status again using CLI](https://cdn.statically.io/gh/TheOdinProject/curriculum/b54d14c5dcee1c6fac61aee02fca7e9ef7ba1510/foundations/git_basics/project_practicing_git_basics/imgs/11.png)


    MacOS users: If your terminal reads *"command not found: code"*, you must head back to [Command Line Basics](https://www.theodinproject.com/paths/foundations/courses/foundations/lessons/command-line-basics-web-development-101) and follow the instructions provided to allow this command to work.

2.  Add "Hello Odin!" to line 3 of README.md and save the file with "Ctrl+S" (or "Command+S" on Mac).

    ![Edit README using text editor](https://cdn.statically.io/gh/TheOdinProject/curriculum/b54d14c5dcee1c6fac61aee02fca7e9ef7ba1510/foundations/git_basics/project_practicing_git_basics/imgs/12.png)


3.  Back in your terminal (or in the fancy built-in terminal in Visual Studio Code with *Ctrl + \`* ), type `git status`. You'll notice that README.md is now shown as not staged or committed.

    ![Check repo status again using CLI](https://cdn.statically.io/gh/TheOdinProject/curriculum/b54d14c5dcee1c6fac61aee02fca7e9ef7ba1510/foundations/git_basics/project_practicing_git_basics/imgs/13.png)


4.  Add README.md to the staging area with `git add README.md`.
5.  Can you guess what `git status` will output now? README.md will be displayed in green text. That means README.md has been added to the staging area. The file hello_world.txt will not show up because it has not been modified since it was committed.

    ![Stage README changes and check repo status again using CLI](https://cdn.statically.io/gh/TheOdinProject/curriculum/b54d14c5dcee1c6fac61aee02fca7e9ef7ba1510/foundations/git_basics/project_practicing_git_basics/imgs/14.png)


6.  Open hello_world.txt, add some text to it, save it and stage it. You can use `git add .` to add all files in the current directory and all subsequent directories to the staging area. Then, type `git status` once more, and everything should now be in the staging area.

    ![Stage all other files in repo and check repo status again using CLI](https://cdn.statically.io/gh/TheOdinProject/curriculum/b54d14c5dcee1c6fac61aee02fca7e9ef7ba1510/foundations/git_basics/project_practicing_git_basics/imgs/15.png)


7.  Finally, let's commit all of the files that are in the staging area and add a descriptive commit message. `git commit -m "Edit README.md and hello_world.txt"`. Then, type `git status` once again, which will output "*nothing to commit*".

    ![Commit repo changes again and check repo status again using CLI](https://cdn.statically.io/gh/TheOdinProject/curriculum/b54d14c5dcee1c6fac61aee02fca7e9ef7ba1510/foundations/git_basics/project_practicing_git_basics/imgs/16.png)


8.  Take one last look at your commit history by typing `git log`. You should now see three entries.

    ![Git Log](https://cdn.statically.io/gh/TheOdinProject/curriculum/b54d14c5dcee1c6fac61aee02fca7e9ef7ba1510/foundations/git_basics/project_practicing_git_basics/imgs/17.png)

#### Push Your Work to GitHub

Finally, let's upload your work to the GitHub repository you created at the start of this tutorial.

1.  <span id="git-push"></span>Type `git push`. To be more specific, type `git push origin main`. Since you are not dealing with another branch (other than *main*) or a different remote (as mentioned above), you can leave it as `git push` to save a few keystrokes. **NOTE: If at this point you receive a message that says "Support for password authentication was removed on August 13, 2021. Please use a personal access token instead.", you have followed the steps incorrectly and cloned with HTTPS, not SSH. Please follow [these steps](https://docs.github.com/en/get-started/getting-started-with-git/managing-remote-repositories#switching-remote-urls-from-https-to-ssh) to change your remote to SSH, then attempt to push to Github.**

    ![Push changes to remote using CLI](https://cdn.statically.io/gh/TheOdinProject/curriculum/b54d14c5dcee1c6fac61aee02fca7e9ef7ba1510/foundations/git_basics/project_practicing_git_basics/imgs/18.png)

2.  Type `git status` one final time. It should output "*Your branch is up to date with 'origin/main'. nothing to commit, working tree clean*".

    ![Check repo status again to confirm local repo is up to date with remote using CLI](https://cdn.statically.io/gh/TheOdinProject/curriculum/b54d14c5dcee1c6fac61aee02fca7e9ef7ba1510/foundations/git_basics/project_practicing_git_basics/imgs/19.png)

3.  When you reload the repository on GitHub, you should see the README.md and hello_world.txt files that you just pushed there from your local machine.

     ![Verify repo changes are on GitHub](https://cdn.statically.io/gh/TheOdinProject/curriculum/b54d14c5dcee1c6fac61aee02fca7e9ef7ba1510/foundations/git_basics/project_practicing_git_basics/imgs/20.png)

</div>

### Note/warning

When trying to make simple changes to the files in your repo, such as attempting to fix a typo in your README.md you might be tempted to make this change directly via Github. However, it is best to avoid this as it will cause issues that require more advanced Git knowledge than we want to go over at this stage (it is covered in a future lesson), for now it is advised to make any changes via your local files then commit and push them using Git commands in your terminal once ready.

### Cheatsheet

This is a reference list of the most commonly used Git commands. (You might consider bookmarking this handy page.) Try to familiarize yourself with the commands so that you can eventually remember them all:

*   Commands related to a remote repository:
    *   `git clone git@github.com:USER-NAME/REPOSITORY-NAME.git`
    *   `git push` or `git push origin main` (Both accomplish the same goal in this context)
*   Commands related to the workflow:
    *   `git add .`
    *   `git commit -m "A message describing what you have done to make this snapshot different"`
*   Commands related to checking status or log history
    *   `git status`
    *   `git log`

The basic Git syntax is `program | action | destination`.

For example,

*   `git add .` is read as `git | add | .`, where the period represents everything in the current directory;
*   `git commit -m "message"` is read as `git | commit -m | "message"`; and
*   `git status` is read as `git | status | (no destination)`.

### Git Best Practices

There's a lot to learn about using Git. But it is worth taking the time to highlight some best practices so that you can be a better collaborator. Git is not only helpful when collaborating with others. It's also useful when working independently. You will be relying more and more on your own commit history in the future when revisiting old code.

Two helpful best practices to consider are **atomic commits** and leveraging those atomic commits to make your commit messages more useful to future collaborators.

An atomic commit is a commit that includes changes related to only one feature or task of your program. There are two main reasons for doing this: first, if something you change turns out to cause some problems, it is easy to revert the specific change without losing other changes; and second, it enables you to write better commit messages.

### Changing the Git Commit Message Editor

If you are using *Visual Studio Code* (and you should be if you're following this curriculum) and you don't want to get stuck writing a commit message in [Vim](https://en.wikipedia.org/wiki/Vim_(text_editor)) because you accidentally used `git commit` without the message flag (`-m`), this command will make Visual Studio Code open a new tab with the ability to write your commit message and an optional description below it: `git config --global core.editor "code --wait"`.

There will be no confirmation or any output on the terminal after entering this command. To make a commit with Visual Studio Code as the text editor, make sure to use the `git commit` command without the `-m` flag. Just type `git commit` and no message after that. Once you do this, a new tab will open. Now you can write your message, and provide more information if you want, right below it. After typing your commit message, save it and exit the tab.

With that out of the way, now you can choose to use either `git commit -m <your message here>` or `git commit` and enter your message with Visual Studio Code!

### Conclusion

You may not feel completely comfortable with Git at this point, which is normal. It's a skill that you will get more comfortable with as you use it.

The main thing to take away from this lesson is the **basic workflow**. The commands you've learned here are the ones you will be using the most often with Git.

Don't worry if you don't know all the commands yet or if they aren't quite sticking in your memory yet. They will soon be seared into your brain as you use them over and over in future Odin projects.

In later Git lessons, we will cover some of the more advanced Git features, such as branches. They will further expand your abilities and make you more productive.

For now, concentrate on using the basics of Git that you've learned here for all of your projects from now on. You will soon know each of the basic Git commands from memory!

### Knowledge Check

This section contains questions for you to check your understanding of this lesson on your own. If you’re having trouble answering a question, click it and review the material it links to.

*   <a class="knowledge-check-link" href="#new-github-repo">How do you create a new repository on GitHub?</a>
*   <a class="knowledge-check-link" href="#github-to-local">How do you copy a repository onto your local machine from GitHub?</a>
*   <a class="knowledge-check-link" href="#default-remote">What is the default name of your remote connection?</a>
*   <a class="knowledge-check-link" href="#origin-push">Explain what `origin` is in `git push origin main`.</a>
*   <a class="knowledge-check-link" href="#main-push">Explain what `main` is in `git push origin main`.</a>
*   <a class="knowledge-check-link" href="#two-stages">Explain the two-stage system that Git uses to save files.</a>
*   <a class="knowledge-check-link" href="#git-status">How do you check the status of your current repository?</a>
*   <a class="knowledge-check-link" href="#git-add">How do you add files to the staging area in git?</a>
*   <a class="knowledge-check-link" href="#git-commit">How do you commit the files in the staging area and add a descriptive message?</a>
*   <a class="knowledge-check-link" href="#git-push">How do you push your changes to your repository on GitHub?</a>
*   <a class="knowledge-check-link" href="#git-log">How do you look at the history of your previous commits?</a>

### Additional Resources

This section contains helpful links to related content. It isn’t required, so consider it supplemental.

*   It looks like this lesson doesn't have any additional resources yet. Help us expand this section by contributing to our curriculum.
