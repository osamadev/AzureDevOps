pipeline {
 agent any

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
    sh 'dotnet build SmartHotel360.PublicWeb.sln'
   }
  }
  stage('Publish') {
        steps {
         /*sh 'npm install'*/
         sh 'dotnet publish -c Release -p:PublishProfile=FolderProfile'
        }
  }
  stage('Archive') {
    steps {
       archiveArtifacts "SmartHotel360.PublicWeb/bin/Debug/netcoreapp3.1/publish/"
    }
  }
}
}
