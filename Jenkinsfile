pipeline {
 agent {label 'master'}
 environment {
   Release_Path = 'SmartHotel360.PublicWeb/bin/Release/netcoreapp3.1/publish/'
   Project_Name = 'SmartHotel360.PublicWeb.proj'
   Solution_Name = 'SmartHotel360.PublicWeb.sln'
 }
 
 stages {
  stage('Checkout') {
   steps {
    git credentialsId: '8da9c8ef-b0ef-46f7-9ac3-90966514be3a', url: 'https://umosaad@dev.azure.com/umosaad/SmartHotel/_git/PublicWeb', branch: 'master'
   }
  }
  stage('Restore PACKAGES') {
   steps {
    sh "dotnet restore"
   }
  }
  stage('Clean') {
   steps {
    sh 'dotnet clean'
   }
  }
  stage('Build') {
   steps {
    sh 'dotnet build ${env.Solution_Name}'
   }
  }
  stage('Publish') {
        steps {
         /*sh 'npm install'*/
         sh 'dotnet publish -c Release -p:PublishProfile=FolderProfile'
         sh 'zip -r SmartHotel.zip ${env.Release_Path}'
        }
  }
  stage('Archive') {
    steps {
     archiveArtifacts '${env.Release_Path}/*.zip'
    }
  }
}
}
