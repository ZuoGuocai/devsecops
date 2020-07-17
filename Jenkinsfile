pipeline {
    agent any
    
    tools {
        maven 'mvn3.6'
        jdk   'java1.8'
    }
    
    environment {
        HARBOR_CREDS = credentials('jenkins-harbor-creds')   
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
}
