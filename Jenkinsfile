@Library('my-shared-library') _

pipeline{

   agent any

   stages{
 
      stage('Git Checkout'){
         
         steps{
         gitCheckout(
           branch: "main",
           url: "https://github.com/ambefrank/javaapp.git"
         )
         }
      }
      stage('Unit Test Maven'){
         
         steps{
            script{

                mvnTest()
            }
         }
      }
        stage('Integration Test Maven'){
         
         steps{
            script{

                mvnintegrationTest()
            }
         }
      }    
   }
}