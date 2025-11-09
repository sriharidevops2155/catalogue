pipeline {   //Here pipeline is the root element
    agent {
        label 'AGENT-1'
    }
    environment{
        appVersion = '' 
    }
    options{
        timeout(time: 30, unit: 'MINUTES')
       // disableConCurrentBuilds()
    }
    // parameters {
    //     string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
    //     text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')
    //     booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')
    //     choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')
    //     password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    // }

    //Build
    stages {
        stage('Read package.json') {
            steps {
                script {
                    // Read the package.json file
                    def packageJson = readJSON file: 'package.json'
                    // Access properties, for example, the version
                    appVersion = packageJson.version
                    echo "Project version: ${appVersion}"
                }
            }
        }
        stage('Install Dependencies') {
            steps {
                script {
                    sh """
                        npm install 
                    """
                }
            }
        }
    }

    post { 
        always { 
            echo 'I will always say Hello again!'
            deleteDir()
        }
        success { 
            echo 'I will say Hello success'
        }
        failure { 
            echo 'I will say Hello Failure'
        }

    }
}