
class Pipeline{
	
	Pipeline(config_file) {
	this.config_file = config_file
	}
	
	def run(options) {
		def pipeline = Pipeline.config.pipeline
		
		if (pipeline == 'usual') {
			usual()
			} else {
				pipeline.run(options)
				}
	}
	
	def usual() {
		
		pipeline{
			agent none
			stages{
				stage('hello_world'){
					agent any
					steps{
						sh 'echo hello_world!'
					}
					post{
						unsucessful{
							error 'could not echo hello_world!'
						}
					}
				}
			}
		}
	}
}


def config = new Config()
def pipeline = new Pipeline('config':config)
pipeline.run
