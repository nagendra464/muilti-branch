import groovy.json.JsonOutput
import groovy.transform.Field
import groovy.json.JsonSlurper

node('Build-server') 
{
  parameters
  {
      string(name: 'Service_Name', defaultValues: 'account-service', description: 'develop by account-service')
      choice(choices: 'master',  description: 'select the branch name', name: 'Branch_Name')
      choice(choices: 'dev', description: 'select the run time environment', name: 'Server_Environment')

  }
    if ("${env.Branch_Name}" == 'master')
  {
     Checkout()
     Build()
  }
}
    def Checkout()
  {
      stage('checkout'){
          checkout scm
      }
  }
    def build()
    {
      stage('build'){
        sh "cd ${params.Service_Name}; mvn clean install"
      }
    }

