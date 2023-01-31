# Part 1 – Configure application

1.	Create a service connection in a Azure DevOps project to your subscription - 
![Savchuk Dmytro](1.png "Service Connection")

2.	Find a .net pet project for the experiments
![Savchuk Dmytro](2.png ".Net project")

3.	Build your app locally .net project via dotnet tool. dotnet restore/build/run
![Savchuk Dmytro](3.png "Build pipeline")

4.	Create an Azure DevOps repo You can use import repository to import from existing source control version like github

Repo was created in previous screenshot and my .NET project was moved inside in pet-project Repo

5.	Create a branching policy for you application. Added yourself as a reviewer. As branching strategy use a github flow (It will be applied by default when you strict commit to your main branch)

Policy was created with reviewer as myself

![Savchuk Dmytro](3.png "Branch policy")


# Part 2 – Configure a pipeline to deploy infrastructure 

1.	Create a separate resource group and deploy azure storage account 

Storage account nad RG were created 
![Savchuk Dmytro](2.1.png "RG and Storage acc")

2.	Create a container with the name “tfstate” and remember the name. use portal settings 

Container and TF state file were created (terraform file created automatically after TF execution)
![Savchuk Dmytro](2.2.png "Container and state file")


# Part 2.2 – Create a terraform pipeline

1.	Create a yaml pipeline with the following steps: terraform install, terraform init, terraform plan/apply. Plan is an optional one 

Pipeline created for terraform execution
![Savchuk Dmytro](2.3.png "Container and state file")

2.	Inside yaml pipeline add trigger to main branch. The scenario – when main is updated, pipeline should run automatically

Main branch is set up for automation
![Savchuk Dmytro](2.4.png "Container and state file")

3.	Added 3 steps – terraform install, terraform init, terraform plan/apply. Plan is an optional one. You may add it as 4th step

Resources which created by terraform
![Savchuk Dmytro](2.5.png "Container and state file")

Terraform manifest
![Savchuk Dmytro](2.6.png "Container and state file")


# Part 3 – Create a deploy pipeline to app service

1.	Add yml pipeline to the application folder

You can see pipeline on 3 screenshot, where we building our application

2.	Your pipeline structure should contain 2 stages. 1st – build, create zip archieve, and publish an artifact. 2nd – download an artifact and deploy it to azure app service 

![Savchuk Dmytro](2.7.png "Container and state file")

3.	To deploy .zip to app service use azure app service deployment task

Same on previous script, separate job for dpeloyment application to app service 

# Service connection 

![Savchuk Dmytro](2.8.png "Container and state file")
