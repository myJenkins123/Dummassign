package first
/*
class configfile {
	static void main(def args) {
		def mylist = [1,2,'usha1']
		mylist.forEach{println it}			
		
	}
}*/
	
class Config {
	def config(config,file) {
		def config_file = "config.yaml"
		def pipeline_config = readConfigFile(config_file)
		return pipeline_config
	}	
	//thi is wat bryan has written
	
	
	
	//line 19 to 24 is what i have tried
	  /*def config(file) {
		  def config_file = readYaml file: "config.yaml"
		  config_file.names = 'hello world!'
		  writeYaml file: 'config.yaml', data: config_file
		  def pipeline_config = readConfigFile(config_file)
		  return pipeline_config
	}*/
	
	def readConfigFile(config_file) {
		pipeline_config = Yaml.load_file(config_file)
		return pipeline_config
	}

}

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
