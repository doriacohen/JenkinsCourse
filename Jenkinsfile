pipeline {
    agent any

    stages {
        stage('Clone Sources') {
            steps {
                checkout scm          
            } 
        }   
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
        stage('Executing Bash script') {
            steps {      
                sh '''
                    if [ "$LANGUAGE" = "Bash" ] || [ "$LANGUAGE" = "All" ]; then
                    cd ${WORKSPACE}/Scripts/
                    chmod 755 bash_project.sh
                    ./bash_project.sh 
                    ./bash_project.sh >> output.txt
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
                      ./python_project.py >> output.txt
                     else
                     echo "$LANGUAGE file is selected! "
                      fi
                   '''
                }
            }
    }
}
