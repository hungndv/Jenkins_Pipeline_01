pipeline {
    agent any 
    stages {
/*// uncomment stage('Checkout') to test on local
        stage('Checkout') {
            steps {
                git credentialsId: 'cb2054a9-9a1e-4074-92b5-ed043797387b', url: 'https://github.com/hungndv/Jenkins_Pipeline_01.git'
            }
        }
*/
        stage('Build') {
            steps {
                bat '"C:/nuget.exe" restore Jenkins_Pipeline_01.sln'
                bat '"C:/Program Files (x86)/MSBuild/14.0/Bin/MSBuild.exe" Jenkins_Pipeline_01.sln'
            }
        }
        stage('Test') {
            parallel {
                stage('Parallel Test 1') {
                    steps {
                        powershell 'Write-Output "Parallel 1 Start $((Get-Date).ToString("yyyyMMdd HHmmss"))"'
                        powershell 'sleep 10'
                        powershell 'Write-Output "Parallel 1 End   $((Get-Date).ToString("yyyyMMdd HHmmss"))"'
                    }
                }
                stage('Parallel Test 2') {
                    steps {
                        powershell 'Write-Output "Parallel 2 Start $((Get-Date).ToString("yyyyMMdd HHmmss"))"'
                        powershell 'sleep 10'
                        powershell 'Write-Output "Parallel 2 End   $((Get-Date).ToString("yyyyMMdd HHmmss"))"'
                    }
                }
                stage('Parallel Test 3') {
                    steps {
                        powershell 'Write-Output "Parallel 3 Start $((Get-Date).ToString("yyyyMMdd HHmmss"))"'
                        powershell 'sleep 5'
                        //error 'Throw error...'
                        powershell 'Write-Output "Parallel 3 End   $((Get-Date).ToString("yyyyMMdd HHmmss"))"'
                    }
                }
                stage('Parallel Test 4') {
                    steps {
                        powershell 'Write-Output "Parallel 4 Start $((Get-Date).ToString("yyyyMMdd HHmmss"))"'
                        powershell 'sleep 10'
                        powershell 'Write-Output "Parallel 4 End   $((Get-Date).ToString("yyyyMMdd HHmmss"))"'
                    }
                }
            }
        }
    }
    post { 
        always { 
            emailext attachLog: true, body: '$DEFAULT_CONTENT', subject: '$DEFAULT_SUBJECT', to: 'hungndv1989@gmail.com'
        }
    }
}