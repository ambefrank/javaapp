@Library('my-shared-library') _

pipeline{

   agent any

   parameters{

      choice(name: 'action', choices: 'create\ndelete', description: 'choose create/Destroy')
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
      stage('Quality Gate Status: Sonarqube'){

         when { expression { params.action == 'create'} }
         
         steps{
            script{

                def SonarQubecredentialsId = 'sonar-api'
                QualityGateStatus(SonarQubecredentialsId)
            }
         }
                
   }
}

