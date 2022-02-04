pipeline {
2
        agent any
3
​
4
        stages {
5
                stage('Clone Sources') {
6
                        steps {
7
                                checkout scm          
8
                        } 
9
                }   
10
                stage('Log File Event') {
11
                        steps {
12
                                sh '''
13
                                    cd ${WORKSPACE}/Scripts/
14
                                    touch output.txt
15
                                    date >> output.txt
16
                                   '''
17
                        }
18
                }
19
                stage('Bash script') {
20
                        steps {      
21
                                sh '''
22
                                        if [ "$LANGUAGE" = "Bash" ] || [ "$LANGUAGE" = "All" ]; then
23
                                        cd ${WORKSPACE}/Scripts/
24
                                        chmod 755 bash_project.sh
25
                                        ./bash_project.sh 
26
                                        cat bash_project.sh >> output.txt
27
                                        else
28
                                        echo "Bash file is not selected! "
29
                                        fi
30
                                        '''
31
                                }
32
                 }  
33
                 stage('Python script') {
34
                        steps {
35
                                sh '''
36
                                    if [ "$LANGUAGE" = "Python" ] || [ "$LANGUAGE" = "All" ]; then
37
                                        cd ${WORKSPACE}/Scripts/
38
                                        chmod 755 python_project.py 
39
                                        python3.9 python_project.py
40
                                        cat python_project.py >> output.txt
41
                                        else
42
                                        echo "Python file is not selected! "
43
                                        fi
44
                                    '''
45
 
