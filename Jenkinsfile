pipeline {
    agent any 
    stages {
        stage('Build') {
            steps {
                bat '"C:/nuget.exe" restore Jenkins_Pipeline_01.sln'
                bat '"C:/Program Files (x86)/Microsoft Visual Studio/2017/BuildTools/MSBuild/15.0/Bin/MSBuild.exe" Jenkins_Pipeline_01.sln'
            }
        }
    }
}