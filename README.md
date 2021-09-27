# Web_Scraper app
Qwick - Sr.DevOps task

1. This repo is for the purpose of demonstrating how to deploy a Scrapy web scraper and a MySQL database together, with docker-compose, on K8s or AWS with K8s.
   Scrapy web scraper will pull info from quotes.toscrape.com and export that to MySql DB. 
   To start all containers and run the app with Docekr, use:

        docker-compose up --build -d

2. MySql container will create a DB "quotes" once container is running and will wait for data export from a Scraper app. 
3. PhpMyAdmin gives GUI over the webpage. The web GUI can be accesseble via: 

        http:\\localhost:30002


4. K8s directory contain all nessesary files to deploy this app on Kubernetes.

5.  Deploying scrapper in k8s on AWS - Ansible: 
  - This playbook will spinup an EC2 on AWS (user will specify region, subnet, AMI, etc), install Minikube, Docker, git, will clone a repo and launch an app.

  User will need to config a Dynamic inventory: 
   - For the dynamic inventory, download ec2.py and ec2.ini from this given URL, and paste in the inventory folder:
                      
                      https://github.com/ansible/ansible/tree/stable-2.9/contrib/inventory

   - Add this path in ansible.cfg    
   - After that, you also need to copy the key.pem for the ec2 instance launch.
   - After copying your key, make it executable by the following command:
                   
                   chmod 600 Key_Name.pem  

   - You also need privilege escalation because in aws we have to configure all the configurations done by the user root only 
       (make sure to check and add if needed to absible.cfg).

              [priviledge_escalation]                             
                become=true
                become_user=root
                become_method=sudo
                become_ask_pass=false
                gather_factrs: no

   -  After this edit your ec2.py (add all relevant info)
   -  Change your python path in my case it is /usr/bin/python3  
   - Save it.     
   After this make this file executable by the following command:
                  
                  chmod +x ec2.py    

6. Finally, run it and enjoy it. 


7. Describe how you would test such an application: 
   
  

8. Describe potential flaws in the design and how you could fix them:
   Since I not a professional Python coder, some DB credentials in python code is exposed, need to learn deeper how to work with python env variables to hide them. 

   Instead of runnig MySql(or any other DB) in the container, which is not reliable for sensitive data, I would use AWS RDS or AWS Aurora, depends on needs and application, to provide more resilient, secure and scalable DB. 



   




