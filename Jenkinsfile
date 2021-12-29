#!groovy
pipeline {
  parameters {
    string(name:'LANGUAGE', description:'Bash')
  }
//   agent { node { label 'slave01' } }
  agent any
  stages {
    stage('Clone Sources') {
        steps {
          checkout scm			
        } 
     }	 
   }
}
