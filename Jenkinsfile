pipeline
{
   agent any
   stages
    {
        stage('Checkout')
        {
            steps
            { 
                 sh "git init"
                 //sh "git clean -ffdx"
                // sh "git remote add origin https://github.com/shankar124/docker-pipeline-demo.git"
                //sh "git clean -ffdx"
               //sh "git clone https://github.com/shankar124/docker-pipeline-demo.git"
                 sh "git pull origin master"
            }
        }
        stage ('Build')
        {
            steps
            {
                 echo "Build Stage"
            }
        }
        
        stage ('Docker Build')
        {
            steps 
            {
               script
                {
               // sh "cd docker-pipeline-demo"
                docker.build('$ecrhost')
                } 
            }
        }
       
        stage ('Docker Push')
        {
            steps 
            {
               script
                {
               // sh "cd docker-pipeline-demo"
                sh("eval \$(aws ecr get-login --no-include-email --region ap-south-1) && docker push $ecrhost/$buildname" )
                } 
            }
        }
    }
    
}
