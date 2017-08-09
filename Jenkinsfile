node {

	stage ('Preparation'){
		checkout scm
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
