pipeline{
    agent any
    stages{
        stage("Restore the dependencies"){
            steps{
                sh "dotnet restore"
            }
        }
        stage("Build the project"){
            steps{
                sh "dotnet build --no-restore"
            }
        }
        stage("Run different project tests"){
            parallel{
                stage("Project1 tests"){
                    steps{
                        sh "dotnet test TestProject1/TestProject1.csproj --no-build --verbosity normal"
                    }
                }
                stage("Project2 tests"){
                    steps{
                        sh "dotnet test TestProject2/TestProject2.csproj --no-build --verbosity normal"
                    }
                }
                stage("Project3 tests"){
                    steps{
                        sh "dotnet test TestProject3/TestProject3.csproj --no-build --verbosity normal"
                    }
                }
            }
        }
    }
}