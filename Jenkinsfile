pipeline {
	agent any

	stages {
		stage('Clone Sources') {
			steps {
			        checkout scm          
			} 
		}   
		stage('Log File Event') {
			steps {
			        sh '''
                                    touch output.txt
				    date >> output.txt
                                   '''
			}
		}
		stage('Executing Bash script') {
			steps {      
				sh '''
					if [ "$LANGUAGE" = "Bash" ] || [ "$LANGUAGE" = "All" ]; then
					cd ${WORKSPACE}/Scripts/
					chmod 755 bash_project.sh
					./bash_project.sh 
					cat bash_project.sh >> output.txt
					else
					echo "$LANGUAGE file is selected! "
					fi
					'''
				}
		 }  
		 stage('Executing Python script') {
			steps {
				sh '''
				    if [ "$LANGUAGE" = "Python" ] || [ "$LANGUAGE" = "All" ]; then
					cd ${WORKSPACE}/Scripts/
					chmod 755 python_project.py 
					python3.9 python_project.py
					cat python_project.py >> output.txt
					else
					echo "$LANGUAGE file is selected! "
					fi
				    '''
				}
			}
		 stage('Executing C exe file') {
			steps {
				sh '''
					if [ "$LANGUAGE" = "C" ] || [ "$LANGUAGE" = "All" ]; then
					cd ${WORKSPACE}/Scripts/
					chmod 755 c_project.c
					gcc c_project.c -o c_project_compiled
					./c_project_compiled 
					cat c_project.c >> output.txt
					else
					echo "$LANGUAGE file is selected! "
					fi
					'''
				}
	  		}  
	}
}
