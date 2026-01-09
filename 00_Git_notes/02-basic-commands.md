# Contents

- [Architecture of Git](#architecture-of-git)
  - [The Three States](#the-three-states)
  - [The basic Git workflow](#the-basic-git-workflow-goes-something-like-this)
- [Installing Git](#installing-git)
  - [Installing on Linux](#installing-on-linux)
  - [Installing on macOS](#installing-on-macos)
  - [Installing on Windows](#installing-on-windows)
  - [Installing from Source](#installing-from-source)
- [First-Time Git Setup](#first-time-git-setup)
  - [Git Config](#git-config)
  - [Your Identity](#your-identity)
  - [Your Editor](#your-editor)
  - [Your default branch name](#your-default-branch-name)
  - [Checking Your Settings](#checking-your-settings)
- [Getting Help](#getting-help)
- [List of Basic Commands](#list-of-basic-commands)
- [Additional Essential Commands](#additional-essential-commands)

## List of Basic Commands

| Task                                 | Command                         |
| ------------------------------------ | ------------------------------- |
| Initializing a repository            | `git init`                      |
| Stages a single file                 | `git add filename.js`           |
| Stages all changes                   | `git add .` or `git add -A`     |
| Viewing the status                   | `git status`                    |
| Viewing short status                 | `git status -s`                 |
| Commits with a one-line message      | `git commit -m "Message"`       |
| Commits all tracked changes          | `git commit -am "Message"`      |
| Creates a new branch                 | `git branch branchName`         |
| Switches to another branch           | `git checkout branchName`       |
| Creates and switches to new branch   | `git checkout -b branchName`    |
| Switches to another branch (new)     | `git switch branchName`         |
| Creates and switches (new syntax)    | `git switch -c branchName`      |
| Lists all branches                   | `git branch`                    |
| Lists all branches (local & remote)  | `git branch -a`                 |
| Deletes the branch                   | `git branch -d branchName`      |
| Force deletes the branch             | `git branch -D branchName`      |
| Merge branch into current branch     | `git merge branchName`          |
| Pushes branch to origin              | `git push -u origin branchName` |
| Cloning a repository                 | `git clone repoUrl`             |
| Adds a new remote called upstream    | `git remote add upstream url`   |
| Push the local changes to remote     | `git push`                      |
| Pull changes from remote             | `git pull`                      |
| Fetch changes from remote            | `git fetch`                     |

## Additional Essential Commands

### Viewing History & Changes

| Task                                 | Command                         |
| ------------------------------------ | ------------------------------- |
| View commit history                  | `git log`                       |
| View compact log                     | `git log --oneline`             |
| View log with graph                  | `git log --graph --oneline`     |
| View changes in working directory    | `git diff`                      |
| View staged changes                  | `git diff --staged`             |
| View changes in specific file        | `git diff filename.js`          |
| Show specific commit details         | `git show commitHash`           |

### Undoing Changes

| Task                                 | Command                         |
| ------------------------------------ | ------------------------------- |
| Unstage a file                       | `git restore --staged filename` |
| Unstage a file (old syntax)          | `git reset HEAD filename`       |
| Discard changes in working directory | `git restore filename`          |
| Discard changes (old syntax)         | `git checkout -- filename`      |
| Amend last commit                    | `git commit --amend`            |
| Reset to previous commit (soft)      | `git reset --soft HEAD~1`       |
| Reset to previous commit (hard)      | `git reset --hard HEAD~1`       |
| Revert a commit                      | `git revert commitHash`         |

### Stashing Changes

| Task                                 | Command                         |
| ------------------------------------ | ------------------------------- |
| Stash current changes                | `git stash`                     |
| Stash with a message                 | `git stash save "message"`      |
| List all stashes                     | `git stash list`                |
| Apply most recent stash              | `git stash apply`               |
| Apply and remove most recent stash   | `git stash pop`                 |
| Apply specific stash                 | `git stash apply stash@{n}`     |
| Drop specific stash                  | `git stash drop stash@{n}`      |
| Clear all stashes                    | `git stash clear`               |

### Remote Operations

| Task                                 | Command                         |
| ------------------------------------ | ------------------------------- |
| List remote repositories             | `git remote -v`                 |
| Add a remote repository              | `git remote add name url`       |
| Remove a remote                      | `git remote remove name`        |
| Rename a remote                      | `git remote rename old new`     |
| Fetch from remote                    | `git fetch origin`              |
| Pull from remote                     | `git pull origin branchName`    |
| Push to remote                       | `git push origin branchName`    |
| Delete remote branch                 | `git push origin --delete branch`|

### Tagging

| Task                                 | Command                         |
| ------------------------------------ | ------------------------------- |
| List all tags                        | `git tag`                       |
| Create a lightweight tag             | `git tag v1.0.0`                |
| Create an annotated tag              | `git tag -a v1.0.0 -m "msg"`    |
| Push tags to remote                  | `git push --tags`               |
| Delete a tag locally                 | `git tag -d v1.0.0`             |
| Delete a tag remotely                | `git push origin --delete v1.0.0`|

### Configuration & Cleanup

| Task                                 | Command                         |
| ------------------------------------ | ------------------------------- |
| Remove untracked files               | `git clean -f`                  |
| Remove untracked files & directories | `git clean -fd`                 |
| Preview what will be removed         | `git clean -n`                  |
| Show configuration                   | `git config --list`             |
| Set global username                  | `git config --global user.name` |
| Set global email                     | `git config --global user.email`|

## [Architecture of Git]

### The Three States

Git has three main states that your files can reside in: _modified_, _staged_, and _committed_:

- Modified means that you have changed the file but have not committed it to your database yet.
- Staged means that you have marked a modified file in its current version to go into your next commit snapshot.
- Committed means that the data is safely stored in your local database.

- **The working tree** is a single checkout of one version of the project. These files are pulled out of the compressed database in the Git directory and placed on disk for you to use or modify.
- **The staging area** is a file, generally contained in your Git directory, that stores information about what will go into your next commit.
- **The Git directory** is where Git stores the metadata and object database for your project. This is the most important part of Git, and it is what is copied when you _clone_ a repository from another computer.

#### The basic Git workflow goes something like this:

1. You modify files in your working tree.
2. You selectively stage just those changes you want to be part of your next commit, which adds _only_ those changes to the staging area.
3. You do a commit, which takes the files as they are in the staging area and stores that snapshot permanently to your Git directory.

- If a particular version of a file is in the Git directory, it's considered **_committed_**.
- If it has been modified and was added to the staging area, it is **_staged_**.
- And if it was changed since it was checked out but has not been staged, it is **_modified_**.

## [Installing Git]

### Installing on Linux

If you want to install the basic Git tools on Linux via a binary installer, you can generally do so through the package management tool that comes with your distribution.

- If you're on Arch Linux, you can install git via `pacman`

```console
$ sudo pacman -S git 
```

- If you're on Fedora (or any closely-related RPM-based distribution, such as RHEL or CentOS), you can use `dnf`:

```console
$ sudo dnf install git
```

- If you're on a Debian-based distribution, such as Ubuntu, try `apt`:

```console
$ sudo apt install git
```

For more options, there are instructions for installing on several different Unix distributions on the Git website, at [https://git-scm.com/download/linux](https://git-scm.com/download/linux).

### Installing on macOS

There are several ways to install Git on a Mac.

- Install git via homebrew

```console
$ brew install git
```

If you want a more up to date version, you can also install it via a binary installer. A macOS Git installer is maintained and available for download at the Git website, at [https://git-scm.com/download/mac](https://git-scm.com/download/mac).

### Installing on Windows

There are also a few ways to install Git on Windows.

- The most official build is available for download on the Git website. Just go to [https://git-scm.com/download/win](https://git-scm.com/download/win) and the download will start automatically.

\*Note: this is a project called Git for Windows, which is separate from Git itself; for more information on it, go to [https://gitforwindows.org](https://gitforwindows.org).

- To get an automated installation you can use the [Git Chocolatey package](https://chocolatey.org/packages/git).

_Note that the Chocolatey package is community maintained._

## [First-Time Git Setup]

Now that you have Git on your system, you'll want to do a few things to customize your Git environment. You should have to do these things only once on any given computer; they'll stick around between upgrades. You can also change them at any time by running through the commands again.

### Git Config

Git comes with a tool called `git config` that lets you get and set configuration variables that control all aspects of how Git looks and operates.

These variables can be stored in three different places:

1. `[path]/etc/gitconfig` file: Contains values applied to every user on the system and all their repositories. If you pass the option `--system` to `git config`, it reads and writes from this file specifically. Because this is a system configuration file, you would need administrative or superuser privilege to make changes to it.
2. `~/.gitconfig` or `~/.config/git/config` file: Values specific personally to you, the user. You can make Git read and write to this file specifically by passing the `--global` option, and this affects _all_ of the repositories you work with on your system.
3. `config` file in the Git directory (that is, `.git/config`) of whatever repository you're currently using: Specific to that single repository. You can force Git to read from and write to this file with the `--local` option, but that is in fact the default. Unsurprisingly, you need to be located somewhere in a Git repository for this option to work properly.

Each level overrides values in the previous level, so values in `.git/config` trump those in `[path]/etc/gitconfig`.

On Windows systems, Git looks for the `.gitconfig` file in the `$HOME` directory (`C:\Users\$USER` for most people). It also still looks for `[path]/etc/gitconfig`, although it's relative to the MSys root, which is wherever you decide to install Git on your Windows system when you run the installer. If you are using version 2.x or later of Git for Windows, there is also a system-level config file at `C:\Documents and Settings\All Users\Application Data\Git\config` on Windows XP, and in `C:\ProgramData\Git\config` on Windows Vista and newer. This config file can only be changed by `git config -f <file>` as an admin.

You can view all of your settings and where they are coming from using:

```console
$ git config --list --show-origin
```

### Your Identity

The first thing you should do when you install Git is to set your user name and email address. This is important because every Git commit uses this information, and it's immutably baked into the commits you start creating:

```console
$ git config --global user.name "John Doe"
$ git config --global user.email johndoe@example.com
```

Again, you need to do this only once if you pass the `--global` option, because then Git will always use that information for anything you do on that system. If you want to override this with a different name or email address for specific projects, you can run the command without the `--global` option when you're in that project.

Many of the GUI tools will help you do this when you first run them.

### Your Editor

Now that your identity is set up, you can configure the default text editor that will be used when Git needs you to type in a message. If not configured, Git uses your system's default editor.

If you want to use a different text editor, such as VS Code, you can do the following:

```console
$ git config --global core.editor code
```

On a Windows system, if you want to use a different text editor, you must specify the full path to its executable file. This can be different depending on how your editor is packaged.

In the case of Notepad++, a popular programming editor, you are likely to want to use the 32-bit version, since at the time of writing the 64-bit version doesn't support all plug-ins. If you are on a 32-bit Windows system, or you have a 64-bit editor on a 64-bit system, you'll type something like this:

```console
$ git config --global core.editor "'C:/Program Files/Notepad++/notepad++.exe' -multiInst -notabbar -nosession -noPlugin"
```

**Note:** Vim, Emacs and Notepad++ are popular text editors often used by developers on Unix-based systems like Linux and macOS or a Windows system. If you are using another editor, or a 32-bit version, please find specific instructions for how to set up your favorite editor with Git in [git config core.editor commands](https://git-scm.com/book/en/v2/ch00/ch_core_editor).

**Warning:** You may find, if you don't setup your editor like this, you get into a really confusing state when Git attempts to launch it. An example on a Windows system may include a prematurely terminated Git operation during a Git initiated edit.

### Your default branch name

By default Git will create a branch called _master_ when you create a new repository with `git init`. From Git version 2.28 onwards, you can set a different name for the initial branch.

To set _main_ as the default branch name do:

```console
$ git config --global init.defaultBranch main
```

### Checking Your Settings

If you want to check your configuration settings, you can use the `git config --list` command to list all the settings Git can find at that point:

```console
$ git config --list
user.name=John Doe
user.email=johndoe@example.com
color.status=auto
color.branch=auto
color.interactive=auto
color.diff=auto
...
```

You may see keys more than once, because Git reads the same key from different files (`[path]/etc/gitconfig` and `~/.gitconfig`, for example). In this case, Git uses the last value for each unique key it sees.

You can also check what Git thinks a specific key's value is by typing `git config <key>`:

```console
$ git config user.name
John Doe
```

**Note:** Since Git might read the same configuration variable value from more than one file, it's possible that you have an unexpected value for one of these values and you don't know why. In cases like that, you can query Git as to the _origin_ for that value, and it will tell you which configuration file had the final say in setting that value:

```console
$ git config --show-origin rerere.autoUpdate
file:/home/johndoe/.gitconfig	false
```

## [Getting Help]

If you ever need help while using Git, there are three equivalent ways to get the comprehensive manual page (manpage) help for any of the Git commands:

```console
$ git help <verb>
$ git <verb> --help
$ man git-<verb>
```

For example, you can get the manpage help for the `git config` command by running this:

```console
$ git help config
```

If you don't need the full-blown manpage help, but just need a quick refresher on the available options for a Git command, you can ask for the more concise "help" output with the `-h` option, as in:

```console
$ git add -h
usage: git add [<options>] [--] <pathspec>...

    -n, --dry-run               dry run
    -v, --verbose               be verbose

    -i, --interactive           interactive picking
    -p, --patch                 select hunks interactively
    -e, --edit                  edit current diff and apply
    -f, --force                 allow adding otherwise ignored files
    -u, --update                update tracked files
    --renormalize               renormalize EOL of tracked files (implies -u)
    -N, --intent-to-add         record only the fact that the path will be added later
    -A, --all                   add changes from all tracked and untracked files
    --ignore-removal            ignore paths removed in the working tree (same as --no-all)
    --refresh                   don't add, only refresh the index
    --ignore-errors             just skip files which cannot be added because of errors
    --ignore-missing            check if - even missing - files are ignored in dry run
    --chmod (+|-)x              override the executable bit of the listed files
    --pathspec-from-file <file> read pathspec from file
    --pathspec-file-nul         with --pathspec-from-file, pathspec elements are separated with NUL character
```
