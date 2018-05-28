
Skip to X if using existing sources for the submodule.

1. Create a new empty GitHub repository that will be used as a submodule.
2. Clone to your PC.
3. In the cloned folder, create a maven project and configure pom.xml as you would with any other maven project.
4. Create modules and push new commits to your GitH ub repository.
5. In your main project (the one using the submodule created above) structure your project as follows:
```
+--top project folder
|  +--submodule
|  +--your project as a subdirectory
```
6. 