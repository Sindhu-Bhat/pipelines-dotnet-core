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
           bat 'dotnet publish pipelines-dotnet-core.csproj -c Release'
      }
   }

    stage('deploy') {
        steps {
        azureWebAppPublish azureCredentialsId: params.azure_cred_id,
            resourceGroup: "myResourceGroup", appName: "jenkinssample", sourceDirectory: "bin/Release/netcoreapp2.2/publish/"
        }
    }

 }
}
