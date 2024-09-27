# What is CI/CD?
- CI or Continuous Integration is the practice of automating the integration of code changes from multiple developers into a single codebase. It is a software development practice where the developers commit their work frequently into the central code repository (Github or Stash). Then there are automated tools that build the newly committed code and do a code review, etc as required upon integration. The key goals of Continuous Integration are to find and address bugs quicker, make the process of integrating code across a team of developers easier, improve software quality and reduce the time it takes to release new feature updates.

- CD or Continuous Delivery is carried out after Continuous Integration to make sure that we can release new changes to our customers quickly in an error-free way. This includes running integration and regression tests in the staging area (similar to the production environment) so that the final release is not broken in production. It ensures to automate the release process so that we have a release-ready product at all times and we can deploy our application at any point in time.

# What Is a Build Job?

A Jenkins build job contains the configuration for automating a specific task or step in the application building process. These tasks include gathering dependencies, compiling, archiving, or transforming code, and testing and deploying code in different environments.
Jenkins supports several types of build jobs, such as freestyle projects, pipelines, multi-configuration projects, folders, multibranch pipelines, and organization folders.

# Freestyle Project

A freestyle project in Jenkins is a type of project that allows you to build, test, and deploy software using a variety of different options and configurations. Here are a few tasks that you could complete when working with a freestyle project in Jenkins.

## Task-01
Create a new Jenkins freestyle project for your app.
1. Log in to Jenkins and navigate to the main dashboard.
2. Click on the "New Item" button to create a new project.
3. Select "Freestyle project" and give the project a name.
4. Click on the "OK" button to create the project.

In the project configuration page, you can specify the details of the project, such as the source code management system, build triggers, and build actions. In GitHub project write your GitHub project repository URL.

In the "Source Code Management" section, you can specify the repository location, such as Git and Select branch name "main"

Add a second step to run the "docker run" command to start a container using the image created in step 3.

