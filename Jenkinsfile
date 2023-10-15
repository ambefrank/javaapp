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
      stage('Maven Test'){
         
         steps{
            script{

                mvnTest()
            }
         }
      }
   }
}