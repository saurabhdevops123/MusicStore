pipeline {
    agent { label 'dotnet6' }
    triggers { pollSCM('* * * * *') }
    stages {
        stage('vcs') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/saurabhdevops123/MusicStore.git'

            }
        }
        stage('build') {
            steps {
                sh 'dotnet restore ./MusicStore/MusicStore.csproj && dotnet build ./MusicStore/MusicStore.csproj'
            }
        }
        stage('test') {
            steps {
                sh 'dotnet test ./MusicStoreTest/MusicStoreTest.csproj dotnet test --logger "junit;LogFilePath=TEST-musicstore.xml"'
                junit testResults '**/test-*.xml'
            }
        }
    }
}