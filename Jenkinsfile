def choiceArray = []
node {
    checkout scm
    def folders = sh(returnStdout: true, script: "ls -R $WORKSPACE")
    
    folders.split().each {
        //condition to skip files if any
        choiceArray << it
    }
}

pipeline {
    agent any;
    parameters { choice(name: 'CHOICES', choices: choiceArray, description: 'Please Select One') }
    stages {
        stage('debug') {
            steps {
                echo "Selected choice is : ${params.CHOICES}"
            }
        }
    }
}
