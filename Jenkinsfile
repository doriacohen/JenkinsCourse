//This is a jenkins file that will pull from the master user.
//I created 4 choice parameters - All, C, Bash and Python. This parameters are saved as $LANGUAGE.

pipeline {
  agent { node { label 'slave01' } } //agent any
  stages {
    stage('Clone Sources') {
        steps {
          checkout scm			
        } 
     }	 
    stage('Executing Bash script') {
      steps {      
        sh '''
          if [ "$LANGUAGE" = "Bash" ] || [ "$LANGUAGE" = "All" ]; then
            cd ${WORKSPACE}/Scripts/
            chmod 755 Bash_script.sh
            ./Bash_script.sh 
            ./Bash_script.sh >> output.txt
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
               chmod 755 Python_script.py
               ${WORKSPACE}/scripts/Python_script.py $LANGUAGE
               ${WORKSPACE}/scripts/Python_script.py $LANGUAGE >> output.txt
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
                chmod 755 C_script.c
                gcc C_script.c -o C_script
		./C_script 
		./C_script >> output.txt
              else
                echo "$LANGUAGE file is selected! "
              fi
            '''
         }
      }      
      stage('Creating log file') {
        steps {
          sh '''
	    logFile="${HOME}/logdir/logFile"
	    mkdir -p ${HOME}/logdir/
            if [ -f "${logFile}" ]; then
                echo "A log file is already exists"
            else
	        touch ${logFile}
            fi
	    cat ${WORKSPACE}/scripts/output.txt > ${logFile}
	    date >> ${logFile}
           '''
         }
      }
   }
}
