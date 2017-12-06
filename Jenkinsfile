node {
   stage("Preparation") {
       git credentialsId: '46cf4ed2-6475-4a2f-b3ab-624817fd51bd', url: 'git@github.com:thomasp85/jenkins-workshop.git'
   }
   stage("Builde") {
       sh 'docker run -i --rm --name my-maven-project -v "$PWD":/usr/src/mymaven -w /usr/src/mymaven maven:3-jdk-8 mvn clean package'
   }
   stage("Javadoc") {
       sh 'docker run -i --rm --name my-maven-project -v "$PWD":/usr/src/mymaven -w /usr/src/mymaven maven:3-jdk-8 mvn site'
   }
   stage("Results") {
       junit '**/target/surefire-reports/TEST-*.xml'
       archiveArtifacts artifacts: 'target/gildedrose-*.jar', onlyIfSuccessful: true
   }
}
