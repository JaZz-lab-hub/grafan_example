- run `docker compose up -d`
- goto `http://localhost:3000`


- Curl usages:
```
curl -u employee:employee http://localhost:3001/employee
curl -u employee:employee http://localhost:3001/user
curl -u employee:employee http://localhost:3001/admin


curl -u admin:admin http://localhost:3001/employee
curl -u admin:admin http://localhost:3001/user
curl -u admin:admin http://localhost:3001/admin


curl -u user:user http://localhost:3001/user
curl -u user:user http://localhost:3001/employee
curl -u user:user http://localhost:3001/admin
```
