- run `docker compose up -d`
- goto `http://localhost:3000`
- user/pwd are: admin/admin
- open a  new tab and goto `http://localhost:1080` to see alert emails
- Simulate high load cpu (adjust if needed): `docker compose exec strss stress-ng --cpu 8 --timeout 30 --metrics-brief`
- Simulate illegal access:

```
# Logged as an Employee
docker compose exec curl curl -u employee:employee http://server-app/employee # authorized
docker compose exec curl curl -u employee:employee http://server-app/user  # authorized
docker compose exec curl curl -u employee:employee http://server-app/admin # unauthorized, alert

# Logged as an Admin
docker compose exec curl curl -u admin:admin http://server-app/employee # authorized
docker compose exec curl curl -u admin:admin http://server-app/user     # authorized
docker compose exec curl curl -u admin:admin http://server-app/admin    # authorized

# Logged as a normal User
docker compose exec curl curl -u user:user http://server-app/user       # authorized
docker compose exec curl curl -u user:user http://server-app/employee   # unauthorized, alert
docker compose exec curl curl -u user:user http://server-app/admin      # unauthorized, alert
```
