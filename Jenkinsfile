node {
    def mvnHome = tool 'Maven3'
    stage ('Checkout'){
        checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Sappireddyraviteja/demjava.git']]])
    }
    
    stage('Build'){
        sh "${mvnHome}/bin/mvn clean install demjava/pom.xml"
    }
    
    stage('Code quality'){
        withSonarQubeEnv('SonarQube'){
            sh "${mvnHome}/bin/mvn clean install demjava/pom.xml"
        }
    }
}
