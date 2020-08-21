pipeline {
 agent any
 environment {
  dotnet = 'path\to\dotnet.exe'
 }
 stages {
  stage('Checkout') {
   steps {
    git credentialsId: '8da9c8ef-b0ef-46f7-9ac3-90966514be3a', url: 'https://umosaad@dev.azure.com/umosaad/SmartHotel/_git/PublicWeb', branch: 'master'
   }
  }
  stage('Restore PACKAGES') {
   steps {
    bat "dotnet restore --configfile NuGet.Config"
   }
  }
  stage('Clean') {
   steps {
    bat 'dotnet clean'
   }
  }
  stage('Build') {
   steps {
    bat 'dotnet build --configuration Release'
   }
  }
