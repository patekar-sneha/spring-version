#!/bin/bash -x

node('master'){

stage ('Build Properties') {
	echo "BUILD NUMBER--->${env.BUILD_NUMBER}"
	echo "WORKSPAE-------> ${workspace}"
}

stage ('Build') {

	checkout scm
	
	bat 'mvn -Drevision=1.0.0.${BUILD_NUMBER} clean install'
	withCredentials([usernamePassword(credentialsId: 'gitCredentialNew', passwordVariable: 'GIT_PASS', usernameVariable: 'GIT_USER')]) {
    dir("${workspace}/"){
    bat ('git init')
   	bat ('git config --global user.email "patekarsneha@gmail.com"')
   	bat ('git config --global user.name "patekar-sneha"')
   	bat ('git remote set-url origin https://${GIT_USER}:${GIT_PASS}@github.com/patekar-sneha/spring-version.git')
   	bat ('git add .')
   	bat('git status')
   	bat('git commit -m "test version"')
   	bat ('git push origin HEAD:master')
   	
    }
}

}


}