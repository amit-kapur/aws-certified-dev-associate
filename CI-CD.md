# Continuous Integration, Continuous Delivery/Deployment 

    1. Software development Best Practice
    2. Make Small Changes and automate everything!
        Small, incremental code changes, Automate as much as possible for example Code Integration, Build, Test and deployment. 
    3. Why is it so cool?
        Large companies have pioneered this approach to release code, successfully applying thousands of changes per day. 

    Shared Code Repository (GIT) --> Automated Build --> Automated Test --> Code is merged into master --> 
    Prepared for deployment --> manual decision OR automatic deployment. 

    - 1. Continuous Integration (CI)
        Integrating or merging code changes frequently - at least once per day. 
        Think CodeCommit

    - 2. Continuous Delivery (Manual)
        Humans are involved in the decision to deploy the code. This is called Continuous Delivery. 

        Automating the build, test and deployment functions. 
        Think CodeBuild and CodeDeploy

    - Continuous Deployment (Automated)
        The system automatically deploys the new code as soon as it has been prepared for deployment. This is known as Continuous Deployment. 
        
        Fully automated release process, code is deployed into Staging or Production as soon as it has successfully passed through the release pipeline. 
        Think CodePipelines. 


    Four Tools available for CI/CD:
        - CodeCommit 
            Source and Version control 
        - CodeBuild
            Automated Build. 
            It compiles source code, runs tests and produces packages that are ready to deploy.
        - CodeDeploy
            Automated Deployment 
            Automates code deployments to any instance, including EC2, Lambda and on-premises. 
        - CodePipelines
            Manages the workflow 
            End-to-end solution, build, test and deploy your application every time there is a code change. 
           

# CodeCommit 

# CodeDeploy

# CodeBuild

# CodePipeline


# Elastic Container Service

