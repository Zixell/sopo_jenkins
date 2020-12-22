# sopo_jenkins

1. Настраиваем агент 'jenkins-agent'
2. Создаем pipeline jenkins-run.В качестве параметра зададим jenkins-pas - пароль суперюзера, используемый в скрипте ansible playbook.
3. В репозитории создадем Jenkinsfile, в нашем примере скрипт будет выводить на консоль, что код обработан

```
node('jenkins-agent'){
    stage('Working') {
        // List source
        sh 'ls .'
        // Run ansible galaxy
        sh 'Code handled'
    }
}
```
4. Настраиваем pipeline jenkins-run так, чтобы в качестве исполняемого скрипта использовался Jenkinsfile.
5. Запустим pipeline. Результат выполнения представлен ниже:

```
Started by user zixel
Obtained Jenkinsfile from git https://github.com/Zixell/sopo_jenkins.git
Running in Durability level: MAX_SURVIVABILITY
[Pipeline] Start of Pipeline
[Pipeline] node
Running on jenkins-agent in /home/jenkins/workspace/jenkins-run
[Pipeline] {
[Pipeline] stage
[Pipeline] { (Working)
[Pipeline] sh
+ ls .
Jenkinsfile
README.md
[Pipeline] sh
+ 'Code handled'
Code handled
[Pipeline] // stage
[Pipeline] // node
[Pipeline] End of Pipeline
Finished: SUCCESS 
```
