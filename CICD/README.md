[![Contributors][contributors-shield]](https://github.com/pinodo)
[![linkedin-shield][linkedin-shield]](https://www.linkedin.com/in/alvin-kim-57302a193/)

<!-- ABOUT THE PROJECT -->
## About The Project

This project is built to understand the basic knowledge of Jenkins and the belows are covered.
* What is CI/CD?
* Jenkins concept and how it runs
* Environment setting and understanding of the basic cycle
* Installation of Jenkins and plugins
* Implementing CI/CD pipeline
* Jenkins in a real environment

### What is CI/CD?
> Continuous Integration: Frequent merging of several small changes into a main branch
>
> Continuous Delivery: When teams produce software in short cycles with high speed and frequency so that reliable software can be released at any time, and with a simple and repeatable deployment process when deciding to deploy
>
> Continuous Deployment: When new software functionality is rolled out completely automatically
>
> => CI/CD bridges the gaps between development and operation activities and teams by enforcing automation in building, testing and deployment of applications

### Advantages of CI/CD
> Allows organizations to ship software quickly and efficiently
> 
> Facilitates an effective process for getting products to market faster than before
> 
> Ensures an ongoing flow of new features and bug fixes
> 
> Automated deployment

### Jenkins
```
1. Runs on Java Runtime Environment
2. Processes various automization using various plugins
3. Build CI/CD pipeline. Pipeline:  A set of the order of automization tasks
```

### Jenkins Plugins
* Credentials Plugin
  * Since Jenkins is just a server, to access to the resources required when deploying, it should contains the various important data
  * Storing these important data (AWS token, Git access token, etc...)
* Pipeline Plugin
  * Enables to manage Pipeline
* Docker plugin and Docker Pipeline

### Pipeline
* Pipeline is a set of plugins to implement the pipeline to Jenkins
* Two types
  * Declarative Pipeline(latest, readable)
  * Scripted Pipeline
* Syntax
  ```shell
  pipeline {
    agent any
    stages {
      stage('Example') {
        steps {
          echo 'Hello World'
        }
      } 
    }
    post {
      always {
        echo 'I will always say Hello again!'
      }
    }
  }
  ```

### Development Environment
* Local environment (individual developer)
* Integration test environment (a team with developers)
* QA environment (QA engineer and internal users)
* Production environment (a real user)

### Development process
1. Individual development
2. Do the internal test to check the code differences with other developers' one
3. Post the codes to git or SCM (usually on the dev branch)
4. Code formatting and test
5. Build
6. Deploy
7. Test

<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[contributors-shield]: https://img.shields.io/github/contributors/pinodo/dev_note.svg?style=for-the-badge
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
