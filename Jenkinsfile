pipeline{
    agent any

    tools {
        dotnetsdk 'dotnet8'
    }

    stages{
        stage("Restore dependencies"){
            steps{
                sh 'dotnet restore'
            }
            post{
                failure{
                    echo "Step failed"
                }
            }
        }
        stage("Build solution"){
            steps{
                sh 'dotnet build --no-restore'
            }
        }
      
        stage("Run tests for Project 1"){
            steps{
                sh 'dotnet test TestProject1/TestProject1.csproj --no-build --verbosity normal'
            }
        }
      
       stage("Run tests for Project 2"){
            steps{
                sh 'dotnet test TestProject2/TestProject2.csproj --no-build --verbosity normal'
            }
        }

       stage("Run tests for Project 3"){
            steps{
                sh 'dotnet test TestProject3/TestProject3.csproj --no-build --verbosity normal'
            }
        }
    }

    post{
        always{
            echo "Workflow completed successfully"
        }
    }
}
