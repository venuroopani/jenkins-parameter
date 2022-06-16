def choiceArray = []
node {
    checkout scm
    def folders = sh(returnStdout: true, script: ""find . -not -path '*/.*' -type f -name '*'"")
    
    folders.split().each {
        //condition to skip files if any
        choiceArray << it
    }
}
def paraArray = []
node {
    checkout scm
    def folders = sh(returnStdout: true, script: "ls -R $WORKSPACE/dir")
    
    folders.split().each {
        //condition to skip files if any
        paraArray << it
    }
}

pipeline {
    agent any;
    parameters {
                choice(name: 'CHOICES', choices: choiceArray, description: 'Please Select One') 
                choice(name: 'PARA', choices: paraArray, description: 'Please Select The APIGateWay')
               }
    stages {
        stage('debug') {
            steps {
                echo "Selected choice is : ${params.CHOICES}"
                echo "Selected APIGateWay is : ${params.PARA}"
            }
        }
    }
}
