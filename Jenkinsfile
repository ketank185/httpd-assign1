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
			stage ("creating_docker_containers_on_Jenkins-master") {
				steps {
				         sh '''
				         		sudo docker run -itdp 80:80 --name httpd-1 httpd
						 		sudo docker run -itdp 81:80 --name httpd-2 httpd
						 		sudo docker run -itdp 82:80 --name httpd-3 httpd
						 	'''
				}
			}
			stage ("copying index file in resp. containers") {
				steps {
		 				sh '''  sudo docker cp $WORKSPACE/index.html httpd-1:/usr/local/apache2/htdocs/
		 				        sudo docker cp $WORKSPACE/index.html httpd-2:/usr/local/apache2/htdocs/
		 					    sudo docker cp $WORKSPACE/index.html httpd-3:/usr/local/apache2/htdocs/
		 				   '''
				}
			}
		}
}
