[//]: # (title: Jenkins)

[Jenkins](https://www.jenkins.io/doc/) is a self-contained, open source server for automation of software-related tasks 
such as building, testing, and deployment of software. To perform tasks, Jenkins uses the
[Pipeline](https://www.jenkins.io/doc/book/pipeline/) functionality.

This guide covers two scenarios for running Qodana inspections with Jenkins:

* Running Jenkins on a host operating system
* Using a dockerized version of Jenkins

## How to start

Pull the Qodana image from Docker Hub (only necessary to update to the `latest` version):

```shell
docker pull jetbrains/qodana-<linter>
```

Here, `linter` denotes a required Qodana linter, see the [Qodana linters](linters.md) page for reference. 

Make sure the [Docker](https://plugins.jenkins.io/docker-plugin/) and 
[Docker Pipeline](https://plugins.jenkins.io/docker-workflow/) plugins are installed on your Jenkins instance.

Below is a Pipeline configuration sample for Jenkins running on a host operating system. This sample uses the `docker` 
agent and specifies the following parameters for it:

* `image` contains the reference to the Qodana image
* `args` provide arguments for running Qodana. The first argument binds the project directory to the `/data/project` 
directory of Qodana. The second argument disables the Qodana image entrypoint 

The `Qodana` stage uses the Qodana image entrypoint `/opt/idea/bin/entrypoint` to start an inspection.

<!-- This configuration does not work properly:
1. It runs Qodana, but using the -v argument is optional, i.e. no inspection is carried out
2. I cannot find the way to bind the inspection report to the host filesystem
This configuration needs to be improved!
-->

```groovy
pipeline {
    agent {
        docker { image 'jetbrains/qodana-<linter>' 
                 args '-v <source-directory>/:/data/project/'
                 args '--entrypoint=""'
        }
    }
    stages {
        stage('Qodana') {
            steps {
                sh '/opt/idea/bin/entrypoint'
            }
        }
    }
}
```

The following sample demonstrates how to run Qodana inspections using a containerized version of Jenkins.

```groovy
Missing_configuration;
```