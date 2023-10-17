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
   }
}