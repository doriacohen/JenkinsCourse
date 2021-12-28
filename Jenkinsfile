pipeline {
  //agent { node { label 'slave01' } }
  agent any
  environment{
	//SERVER_CREDENTIALS = credentials('SECRET_TEXT')
	VERSION = "1.0.0.1"
	
  }

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
                label 'slave'
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
	  
	  stage('Powershell') {
			agent {
                label 'Windows'
            }
	     when {
			expression {
				env.Language=="Powershell" || env.Language=="All"
			}
		 }
         steps {
            echo 'Powershell stage running'
			powershell '''
				Write-Output "from powershell step on Node: $($env:COMPUTERNAME)"
				
				#Write-Host "Get-Variable -Scope Global"
				#Get-Variable -Scope Global
				#Write-Host "Get-ChildItem env:"
				#(gci env:*).GetEnumerator() | Sort-Object Name | Out-String
				
				Set-Location -Path (Join-Path ($env:WORKSPACE) -ChildPath Scripts)
				#Get-ChildItem
				Invoke-Expression -Command (Get-Content -Path powershell.ps1)
			'''
		}
		 
      }//stage('Powershell')
      
   }//stages
   
}//pipeline
