- Steps
1.Start front - docker run -p 8080:80 front 
2.Start db - docker-compose up -d
Change appsetting.json
3.Start back - docker run -d -p 5034:5034 back

