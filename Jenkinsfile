pipeline{
    agent {
           node {
                 label 'buil-in'
                 customWorkspace "/mnt"
                }
          }
    environment{
          PATH ="/data/server/apache-maven-3.8.5/bin:$PATH"
               }
    stages{ 
    	   stage('CLEAN'){
                          steps{
                    			sh "rm -rf *"
                               }
                         }
           stage('clone'){
						  steps{
								sh "git clone https://github.com/Kunaldange0071/project.git" #DBS-ENDPOINT-CONFIGURE-IN-FILE
							   }
                         }
		   stage('build'){
						  steps{
                               dir ('/mnt/project'){
                                                    sh "mvn install"
                                                   }
                               }             
                         }				 
           stage('war-copy'){
                            steps{
                                  dir('/mnt/project/target'){
                                                             sh "cp -r LoginWebApp.war "
                                                            }
                                 }
                            }
           stage('clone&run-war-playbook-dockerfile'){
                                                 steps{
                                                       dir ('/mnt'){
                                                                    sh "sudo su - sysadmin"
																    sh "git clone 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"
											                        sh "ansible-playbook master.yaml"
                                                                   }
                                                      }
                                                     }    
            }      
       }
