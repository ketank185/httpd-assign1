pipeline {
	agent any
		stages {
			stage ("clean_workspace") {
				steps {
					cleanWs ()
				}
			}
			stage ("checkout_code_from_SCM") {
				steps {
					checkout scm
				}
			}
			stage ("creating_docker_container and index deploy_on_container_Jenkins-master") {
				steps {
				         sh " sudo docker run -itdp 80:80 --name httpd-1 httpd "
				}
			}
			stage ("copying index file in resp. containers") {
				steps {
		 		       sh "sudo docker cp $WORKSPACE/index.html httpd-1:/usr/local/apache2/htdocs/"
				}
			}
		}
}
