#!/bin/bash -x

node('master'){

stage ('Build Properties') {
	echo "BUILD NUMBER--->${env.BUILD_NUMBER}"
}

stage ('Build') {

	checkout scm
	
	bat 'mvn clean install -Dbuild.number=${BUILD_NUMBER}'

}


}