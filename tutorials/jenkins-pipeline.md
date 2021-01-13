---
title: Create Jenkins Pipelines
description: This tutorial explains how to create Jenkins pipelines.
---

### Jenkins pipeline

A pipeline is a collection of jobs that brings the software from version control into the hands of the end-users by using automation tools. It is a feature used to **incorporate continuous delivery** in our software development workflow.

Over the years, there have been multiple Jenkins pipeline releases including, Jenkins Build flow, Jenkins Build Pipeline plugin, Jenkins Workflow, etc.

**key features of plugins**

- They represent multiple Jenkins jobs as one whole workflow in the form of a pipeline.
- What do these pipelines do? These pipelines are a **collection of Jenkins jobs** that trigger each other in a specified sequence.

### Jenkinsfile

A Jenkinsfile is a text file that stores the entire workflow as code and it can be checked into a SCM on your local system. This enables the developers to **access, edit and check the code at all times**.

The Jenkinsfile is written using the Groovy DSL and it can be created through a text/groovy editor or through the configuration page on the Jenkins instance.

**Different types of Jenkins pipeline**

The Jenkins pipeline is written based on two syntaxes, namely:

1.**Declarative pipeline syntax**

2.**Scripted pipeline syntax**

### Creating Jenkins pipeline

**Step 1**: Log into Jenkins and select `New item` from the dashboard.

![](_images/new-item.png)

**Step 2**: Enter a name for your pipeline and select `Pipeline` project. Click on `OK` to proceed.

![](_images/pipeline-demo.png)



**Step 3**: Scroll down to the pipeline and choose if you want a Scripted Pipeline (Pipeline Script) or Declarative pipeline(Pipeline Script from SCM).

![](_images/pipeline-option.png)

**Scripted Pipeline (Pipeline Script) :**

**Step 1**: If you want a scripted pipeline then choose ‘pipeline script’ and start typing your code.

Following is an example script that you can use:

```
#!/usr/bin/env groovy
pipeline {
    agent any    
    stages {
        stage('stage one') {
            steps {
                script {
                    tags_extra = "value_1"
                }
                echo "tags_extra: ${tags_extra}"
            }
        }
        stage('stage two') {
            steps {
                echo "tags_extra: ${tags_extra}"
            }
        }
        stage('stage three') {
            when {
                expression { tags_extra != 'bla' }
            }
            steps {
                echo "tags_extra: ${tags_extra}"
            }
        }
    }
}
```

Finally click on `Apply` and `Save`. You have successfully created your first Jenkins pipeline.

![](_images/pipeline-save.png)



**Declarative pipeline(Pipeline Script from SCM) :**

**Step 1**:  If you want a declarative pipeline then select ‘pipeline script from SCM’ and choose your SCM. In this demo you will use Git. Enter your repository URL where you have kept your Jenkisfile.

![](_images/pipeline.png)

**Step 2:**Select the Branch. Within the script path is the name of the `Jenkinsfile` that is going to be accessed from your SCM to run.

![](_images/scm.png)

Finally click on `Apply` and `Save`. You have successfully created your first Jenkins pipeline.

### Build Pipeline

Click on `Build Now` 

![](_images/build-now.png)

You will see a stage view:

![](_images/stage-viiew.png)

Click on particular build like `#1` or `#2` and chose `Console Output` to see the Output.

![](_images/console-output.png)

Below is a sample output:

![](_images/output.png)

Here you go ! You've created a pipeline successfully.