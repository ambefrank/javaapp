@Library('my_shared_library') _

pipeline{

    agent any
    tools {
      jdk 'JDK8'
    }

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
        stage('Unit Test Maven'){
         
           steps{

              script{

                 mvnTest()
              }
           }
        }
    }
}