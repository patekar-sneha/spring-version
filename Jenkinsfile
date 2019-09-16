#!/bin/bash -x

node('master'){

stage ('Build Properties') {
	echo "BUILD NUMBER--->${env.BUILD_NUMBER}"
	echo "WORKSPAE-------> ${workspace}"
}

stage ('Build') {

	checkout scm
	
	bat 'mvn clean install -Ptest -Dbuild.number=${BUILD_NUMBER}'
	withCredentials([usernamePassword(credentialsId: 'git', passwordVariable: 'GIT_PASS', usernameVariable: 'GIT_USER')]) {
    dir("${workspace}/"){
    bat ('git init')
   	bat ('git config --global user.email "patekarsneha@gmail.com"')
   	bat ('git config --global user.name "patekarsneha"')
   	bat ('git remote set-url origin https://github.com/patekar-sneha/spring-version.git')
   	bat ('git add .')
   	bat('git status')
   	bat('git commit -m "test version"')
   	bat ('git push origin HEAD:master')
   	
    }
}

}


}