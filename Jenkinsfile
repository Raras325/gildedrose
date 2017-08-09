node {

	stage ('Preparation'){

		git credentialsId: '7304890d-0418-47c0-b592-f3cc5d4c3c0f', url: 'https://github.com/Raras325/gildedrose.git'

	}

	stage ('Build'){
		sh 'docker run -i --rm -v $PWD:/usr/src/mymaven -w /usr/src/mymaven maven:3-jdk-8 mvn clean package'
	}
	stage ('Results'){

		junit '**/target/surefire-reports/TEST-*.xml'
		archiveArtifacts 'target/gildedrose-*.jar'
		archiveArtifacts '**/target/surefire-reports/TEST-*.xml'
	}

	stage ('Javadoc'){

		sh 'docker run -i --rm -v $PWD:/usr/src/mymaven -w /usr/src/mymaven maven:3-jdk-8 mvn site'
		archiveArtifacts 'target/site/**'
	}

}
