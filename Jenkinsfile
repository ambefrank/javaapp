@Library('my-shared-library') _

pipeline{

   agent any

   parameters{

      choice(name: 'action', choices: 'create\ndelete', description: 'choose create/Destroy')
      string(name: 'ImageName', description: 'name of the docker build', defaultValue: 'javapp')
      string(name: 'ImageTag', description: 'tag of the docker build', defaultValue: 'v1')
      string(name: 'AppName', description: 'name of the Application', defaultValue: 'springboot')
   }

   stages{

      stage('Git Checkout'){
         when { expression { params.action == 'create'} }        
         steps{
         gitCheckout(
           branch: "main",
           url: "https://github.com/ambefrank/javaapp.git"
         )
         }
      }
      stage('Unit Test Maven'){

         when { expression { params.action == 'create'} }
         
         steps{
            script{

                mvnTest()
            }
         }
      }
      stage('Integration Test Maven'){

         when { expression { params.action == 'create'} }
         
         steps{
            script{

                mvnintegrationTest()
            }
         }
      }
      stage('Static Code Analysis: Sonarqube'){

         when { expression { params.action == 'create'} }
         
         steps{
            script{

                def SonarQubecredentialsId = 'sonar-api'
                staticCodeAnalysis(SonarQubecredentialsId)
            }
         }
      }
      stage('Quality Gate Status Check: Sonarqube'){

         when { expression { params.action == 'create'} }
         
         steps{
            script{

                def SonarQubecredentialsId = 'sonar-api'
                QualityGateStatus(SonarQubecredentialsId)
            }
         }
      }
      stage('Maven Build: Maven'){

         when { expression { params.action == 'create'} }
         
         steps{
            script{

                mvnBuild()
            }
         }
      }
      stage('Docker Image Build'){

         when { expression { params.action == 'create'} }
         
         steps{
            script{
               
                DockerBuild("${params.ImageName}", "${params.ImageTag}", "${params.AppName}")
            }
         }
      }          
   }
}