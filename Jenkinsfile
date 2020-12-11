pipeline {
agent any
environment {
dotnet = 'path\\to\\dotnet.exe'
}
stages {
stage ('Checkout') {
            steps {
                 git url: 'https://github.com/Sindhu-Bhat/pipelines-dotnet-core',branch: 'master'
            }
}
stage ('Restore PACKAGES') {     
         steps {
             batch "dotnet restore"
          }
        }
stage('Build') {
     steps {
            bat 'dotnet build --configuration Release'
      }
   }
   stage('Publish') {
     steps {
           bat 'dotnet publish  --configuration Release'
      }
   }
 }
}
