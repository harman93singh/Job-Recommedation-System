# Job-Recommedation-System
Job Recommedation System for our Capstone Project

Download and deploy 2 docker containers for setting up the environment



Create a Bridged Network for connecting Postgres and Django Container...............


 ---->>  " docker network create dj-post "      //dj-post = name of bridged network ...............
 
 
  
Pull Django Docker Container :::......... 


-------->>>> " docker pull hsingh1993/django:final"     ..............


Create Volume /ML as shared volume between host and containers................



Start Django Container :::.................


 
----->>>> " docker run -d --name dj_con --hostname=dj_prod -v /ML:/ML -p 80:8000 --network=dj-post hsingh1993/django:final "............




Pull Postgres Container ::::.............



-------->>> " docker pull hsingh1993/postgres:post "...........



Start Postgres Container ::::.........




---->>> " docker run -d --name post --hostname=post -e POSTGRES_PASSWORD=root123 --network=dj-post -v /ML:/ML hsingh1993/postgres:post "..............



Enter the Django Container to change some configuration :: .............




--->>> " docker exec -it dj_con /bin/bash "...................





---->>> " cd django_app "   ,,,, "cd job_recommendation_system " ,,, " cd  job_scrapper" ,,, " vi settings "..................





Edit settings to provide postgres db name, username and ip..................



Start Django :::.....................




------>> " cd django_apps ",,,, "cd job_recommendation_system " ,,, " cd  job_scrapper" ,,, " vi settings"" >> allowed_host = [dj_con ip]..................




------>> " cd ../ "....................



------->> " python manage.py runserver dj_con_ip:8000 ".......................



OPEN application at web browser ...........................


---->> localhost/IP:80..............................


    
