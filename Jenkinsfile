@Library('my_shared_library') _

pipeline{

    agent any

    stages{
 
        stage('Git Checkout'){
         
           steps{

              script{

                 gitCheckout(
                    branch: "main",
                    url: "https://github.com/ambefrank/javaapp.git"
                 )
              }
           }
        }
    }
}