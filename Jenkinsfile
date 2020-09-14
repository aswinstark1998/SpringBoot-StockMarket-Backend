node{
	stage('Git Checkout'){
		git credentialsId: 'git-cred', url: 'https://github.com/aswinstark1998/SpringBoot-StockMarket-Backend.git/'
	}
	
	stage('MVN Package'){
	    bat "mvn clean install -DskipTests=true"
	}
	
	stage('Build Docker image'){
	    bat 'docker build -t aswindockercontainers/spring-boot-stock-market .'
	}
	
	stage('Push Docker Image'){
	    withCredentials([string(credentialsId: 'docker-hub-passwprd', variable: 'dockerHubPassword')]) {
            bat "docker login -u aswindockercontainers -p ${dockerHubPassword}"
        }
	    
	    bat 'docker push aswindockercontainers/spring-boot-stock-market '
	}
}