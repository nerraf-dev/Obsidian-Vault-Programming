# Git submodules

I am working on a (42) project called Pipex. It allows me to use my `libft` library as well as `ft_printf` **and** any versions I have made of it.

I wondered how to use these within my project. I could open up my previous projects, build the libraries and copy them across. I could copy the source code to the new project and build as a whole. What happens if those libraires get updated in the future? Could I clone the repositories into the new project?

Well I decided I wanted to just clone the existing projects into this one...BUT I found out there's a bit more to it than just doing a `git clone`.

## Submodules

So I found out that I can use submodules. A Git submodule is basically a Git repository embedded within another repository. This means that you can include other repositories in a project, while keeping the advantages of maintaining a repository independently. This works well for what I need especially as the other repos are mine. 

I read into it a bit further and there's more to it than just cloning the other repository and I read about the `git submodule add` command.
