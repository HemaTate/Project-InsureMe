# $${\color {red} \textbf {Batch B35 Jenkins Pipeline Code😃}}$$
![Screenshot (335)](https://github.com/user-attachments/assets/3b7b7534-d798-49ac-abfd-ba2d88030786)

1. $${\color {blue} \textbf {freestyle project🏴‍☠️}}$$
2. $${\color {green} \textbf {pipeline project}}$$
   - docker
   - maven
   - git
```bash
yum install nginx
```

```groovy
pipeline {
    agent any
    tools {
        maven 'maven'
    
    }
    stages {
        stage('code-checkout'){
            steps{
               git branch: 'main', changelog: false, credentialsId: 'github-cred', poll: false, url: 'https://github.com/abhipraydhoble/Project-InsureMe.git' 
            }
        }
        
        stage('code-build'){
            steps{
                sh 'mvn clean package'
            }
        }
        
        stage('doc-image'){
            steps{
                 sh 'docker build -t abhipraydh96/b35 .'
            }
        }
        stage('code-deploy'){
            steps{
                sh 'docker run -itd --name p35 -p 8089:8081 abhipraydh96/b35'
            }
        }
    }
}
```
