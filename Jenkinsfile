node {
    def mvnHome = tool 'Maven3'
    stage ('Checkout'){
        checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Sappireddyraviteja/demjava.git']]])
    }
    
    stage('Build'){
        bat "${mvnHome}/bin/mvn clean install demjava/pom.xml"
    }
    
    stage('Code quality'){
        withSonarQubeEnv('SonarQube'){
            bat "${mvnHome}/bin/mvn clean install demjava/pom.xml"
        }
    }
}
