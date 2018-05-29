
## Adding a Maven project as a git submodule to another Maven project

### Using an **existing MAVEN project** as a submodule

1. Create a new empty GitHub repository that will be used as the submodule.
1. Go to your submodule maven project folder, and run
```
$ git init

$ git remote add origin <Your git repository address>
```

Start to step 5 in the next section.

### Creating a new submodule from scratch

1. Create a new empty GitHub repository that will be used as the submodule.
1. Clone to your PC.
1. In the cloned folder, create a maven project and configure pom.xml as you would with any other maven project. 
1. Create modules and push new commits to your GitHub repository.
1. In your main project (the one that will use the submodule created above) structure your project as follows:
```
+-- top project folder
|   +--your main project
|   |   +--pom.xml
+-- pom.xml
```

6. Go to the top project folder and run
```
$ git submodule add <submodule repository>
```

Your project structure should now be:
```
+-- top project folder
|   +--submodule
|   |   +--pom.xml
|   +--your main project
|   |   +--pom.xml
+-- pom.xml
```

7. In pom.xml in the top project folder, add the following:
    
```
    <modules>
        <module>your main project</module>
        <module>submodule</module>
    </modules>
```
8. In pom.xml in your main project folder, add your submodule as a dependency:
```
        <dependency>
            <groupId>submodule</groupId>
            <artifactId>submodule</artifactId>
            <version>1.0-SNAPSHOT</version>
        </dependency>
```
9. When submodule code is updated:
```
$ cd top_project_folder/submodule_folder

$ git pull

$ cd ..

$ git add .

$ git commit -m "Get latest submodule"

$ git push
```
10. When packaging your Maven project
   1. Go to the top project folder, then run `mvn install`
   3. Go to your main project folder, then run `mvn package`.
