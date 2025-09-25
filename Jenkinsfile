
Jenkinsfile (Declarative Pipeline)

/* Requires the Docker Pipeline plugin */
pipeline {
    agent { docker { image 'python:3.13.7-alpine3.22' } }
    stages {
        stage('build') {
            steps {
                sh 'python --version'
            }
        }
	stage('test') {
	    steps {
		script {
		    def version = sh(script: "python3 -c 'import sys; print(\"{}.{}\".format(sys.version_info[0], sys.version_info[1]))'",returnStdout:true).trim()
		    echo "Detected Python version: ${version}"
		    def(major, minor) = version.tockenize(".").collect {it as int}
		    if (major < 3  || (major == 3 && minor < 7)) {
			error "Python version is less than 3.7. Falling the build."
		    } else {
			println("Python version pass")
		    }
 		}
	    }
	}
    }
}
