@Library('jenkins-shared-library') _ 

def config = [
    project: "roboshop",
    component: "catalogue"
]
if (! env.BRANCH_NAME.equalsIgnoreCase('main')) {
      nodejsEKSPipeline(config) //by default it will call, call function inside this pipeline 
}
else {
    echo "please proceed with PROD process"
}
   