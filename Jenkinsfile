@Library('my_shared_library') _

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
   }
}