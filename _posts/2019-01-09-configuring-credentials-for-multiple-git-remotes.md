---
title: "Configuring credentials for multiple git remotes"
class: wide
---



__Problem__: Using multiple git remote services with Windows Subsystem for Linux.

Recently, I've been trying to really understand version control with git in the context of common remote servers, such as [GitHub](https://github.com/) and [GitLab](https://gitlab.com/).

While GitHub is probably the most popular git remote server, especially for open source projects, it does have something of a downside: you have to pay for private repositories. Generally, I don't like private repositories for open science, but when working on a manuscript, a private repo can be quite nice.

GitLab, on the other hand, provides free private repositories. So, it is a natural ally for hosting all the parts and pieces of a paper in the context of version control, while keeping that information under wraps until the publication has been accepted.

Note: I could have just used local version control with git, but I really wanted to learn how to use some of the online tools.

In the context of git, I've been using Windows Subsystem for Linux (WSL). This means a full-on Linux-like experience for using git. While I could just use [Git for Windows](https://gitforwindows.org/), I'm trying to better understand Linux, so am trying to stay within WSL as much as possible. However, I came up against a problem when trying to use both GitHub and GitLab from git in WSL: user credentials. I won't bore you with the details, but there are some challenges when trying to manage multiple servers at the same time within git. If I were in a purely Linux environment, with a graphical user interface, I could use Git Credential Manager. But, as I understand it, that's not a viable option for WSL.

My solution, then, was to follow [this advice](https://www.edwardthomson.com/blog/git_credential_manager_with_windows_subsystem_for_linux.html) and invoke a windows-based git credential manager from within WSL (one of the coolest parts of WSL is being able to do this).

This has worked super well.

Assuming WSL is configured, here are the instructions for installing a Windows-based git credential manager for WSL-based git:

1. Download Git for Windows: [https://gitforwindows.org/](https://gitforwindows.org/)
2. Open WSL.
3. Run this line: `git config --global credential.helper "/mnt/c/Program\ Files/Git/mingw64/libexec/git-core/git-credential-manager.exe"`
  * Note the "\ " in "Program Files" is used as an escape, as spaces are not valid for Linux/Unix commands (as far as I understand it).
4. `pull` or `push` something to the remote server of your choice.
5. Look for a graphical pop-up from the remote server.
6. Enter your credentials.
7. Done!

I did get an email from GitHub indicating that a personal access token had been added to my account.

The one problem I ran into was my anti-virus software, Kaspersky, which does not like anything running anything associated with the internet from WSL; I kept getting an error while Kaspersky was running, so temporarily disabled it while interacting with my remote servers.

Other than that no problems. Hopefully your configuration was as smooth as mine!
