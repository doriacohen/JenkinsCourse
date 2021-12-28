pipeline {
  agent { node { label 'slave01' } }
//   agent any
//   environment{
// 	//SERVER_CREDENTIALS = credentials('SECRET_TEXT')
// 	VERSION = "1.0.0.1"
	
//   }

   stages {
      stage('Clone Sources') {
        steps {
          checkout scm
        } 
      }//stage('Clone Sources')
	  
	  stage("Env Variables") {
            steps {
				//echo "${env.Language}"
                sh "printenv"
            }
			
        }//stage("Env Variables")
	  
      stage('All') {
		 when {
			expression {
				env.Language=="All"
			}
		 }
         steps {
            echo 'ALL stage running'
            sh 'echo "My first pipeline"'
            sh '''
                echo "By the way, I can do more stuff in here"
                ls -la ~
            '''
         }
      }//stage('All')
	  
      stage('Python') {
	     when {
			expression {
				env.Language=="Python" || env.Language=="All"
			}
		 }
         steps {
            echo 'Python stage running'
         }
      }//stage('Python')
	  
      stage('Bash') {
	     when {
			expression {
				env.Language=="Bash" || env.Language=="All"
			}
		 }
         steps {
            echo 'Bash stage running'
         }
		 
      }//stage('Bash')
	  
	  stage('C') {
			agent {
                label 'slave01'
            }
	     when {
			expression {
				env.Language=="C" || env.Language=="All"
			}
		 }
         steps {
            echo 'C stage running'
         }
		 
      }//stage('C')
      
   }//stages
   
}//pipeline
