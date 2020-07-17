

> 凭据--系统--全局凭据--添加凭据

---



| type |use for |

|:----:|:----:|

|username password | github,docker registry|

|secret text |  dingding|




```
pipeline {
    agent any
    
    tools {
        maven 'mvn3.6'
        jdk   'java1.8'
    }
    
    environment {
        HARBOR_CREDS = credentials('jenkins-harbor-creds') 
        ding_key = credentials('dingding_key')
        DINGDING_ROBOT_URL = 'https://oapi.dingtalk.com/robot/send?access_token='
        Registry_url = "https://registry.zuoguocai-inc.com"
        Build_url = "https://myci.zuoguocai-inc.com"
        

    }
    
    stages {
        
        stage('拉取代码') { // for display purposes
            steps{
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: '3519b4b1-47fd-43e7-bec3-502aa5d5a99a', url: 'https://config-backup.zuoguocai-inc.com/backup-group/mvn-demo.git']]])
            
            }
        }
        stage('编译代码') {
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }
        
 
         
        
        
         stage('构建镜像'){
         
            input {
                message "测试环境"
                ok "提交."
                submitter "alice,bob"
                parameters {
                    string(name: 'PASSWD', defaultValue: '', description: '请输入密码开始部署')
                }
            }
         
         
         
            steps {
            
              script{
              if (PASSWD == HARBOR_CREDS_PSW) {
                echo "start build image"
                
                dir('') {
                    // 删除之前构建镜像
                    sh 'docker rmi registry.zuoguocai-inc.com/zuoguocai-it/springboot:v1'
                    // build镜像
                    sh 'docker build -t registry.zuoguocai-inc.com/zuoguocai-it/springboot:v1 .'
                    // 登录镜像仓库
                    sh 'docker login -u ${HARBOR_CREDS_USR} -p ${HARBOR_CREDS_PSW} registry.zuoguocai-inc.com'
                    // 推送镜像到镜像仓库
                    sh 'docker push registry.zuoguocai-inc.com/zuoguocai-it/springboot:v1'
                   
                }
                
                
                 } else {
                     echo '密码错误,部署失败'
                  }
                }
            }
        }
    }
    
    
post {
    success {
      script {
        def rawmsg = successNotifyData()
        sh "curl -H 'Content-Type:application/json' -X POST --data '${rawmsg}' ${env.DINGDING_ROBOT_URL}${env.ding_key}"
      }
    }

    failure {
      script {
        def rawmsg = failNotifyData()
        sh "curl -H 'Content-Type:application/json' -X POST --data '${rawmsg}' ${env.DINGDING_ROBOT_URL}"
      }
    }
 } 	
  
    
    
}




def failNotifyData() {
  def title = "YourAppName 构建失败[${env.BUILD_NUMBER}]"
  def markdown = "### ${title}\n #### 摘要 >  Image Repo: ${env.registry_url} \n > [点击查看](${env.registry_url})"
  return buildJSON(title, markdown)
}

def successNotifyData() {
  def url = "${env.BUILD_URL}/Package/YourAppName/YourAppName.ipa";
  def title = "YourAppName 构建成功 [${env.BUILD_NUMBER}]"
  def markdown = "### ${title}\n #### 构建结果: \n * [sprintboot](${Registry_url}) \n > buildUrl: ${env.BUILD_URL} \n"
  if(env.UPLOAD_PGY == 'true') {
  	def downloadUrl = createPGYDownloadURL()
  	def qrUrl = createPGYQRURL()
  	markdown = "### ${title}\n #### 构建结果: \n * [YourAppName.ipa](${url}) \n * buildUrl: ${env.BUILD_URL} \n * pgyUrl: ${downloadUrl}\n ${qrUrl}"
  }
  return buildJSON(title, markdown)
}

def buildJSON(title, markdown) {
  return """
  {
    "msgtype": "markdown",
    "markdown": {
      "title":"${title}",
      "text":"${markdown}"
    }
  }
  """
}


def buildTime = new Date().format('yyMMddhhMM', TimeZone.getTimeZone('GMT+8:00'));


```
