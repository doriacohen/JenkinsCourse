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
               ${WORKSPACE}/Scripts/python_project.py $LANGUAGE
               ${WORKSPACE}/Scripts/python_project.py $LANGUAGE >> output.txt
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
                gcc c_project.c -o c_project
		./c_project 
		./c_project >> output.txt
              else
                echo "$LANGUAGE file is selected! "
              fi
            '''
         }
      }      
//       stage('Creating log file') {
//         steps {
//           sh '''
// 	    logFile="${HOME}/logdir/logFile"
// 	    mkdir -p ${HOME}/logdir/
//             if [ -f "${logFile}" ]; then
//                 echo "A log file is already exists"
//             else
// 	        touch ${logFile}
//             fi
// 	    cat ${WORKSPACE}/scripts/output.txt > ${logFile}
// 	    date >> ${logFile}
//            '''
//          }
//       }
   }
}
