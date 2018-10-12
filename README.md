# Secure software design

The aim of this project is to create a forum which is mostly secure using the techniques learned in IMT3501.

## Group members

| Name       | Email                 |
| ---------- | --------------------- |
| Eivind     | eivind@aunebakk.no    |
| Uran       | uhajzeraj@hotmail.com |
| Knut       | kgrstad@gmail.com     |
| Yngve      | yjhestem@stud.ntnu.no |
| Ole Martin | barskern@outlook.com  |

## Installing and running

This project is configured to run as multiple docker containers. By running the following command you will compile and start up all the required services.

```
docker-compose up
```

Find the IP of the `security-gate` using `docker inspect forum_security-gate_1`, and go to `http://<security-gate-ip>/index.html`.

A command which returns the IP-address of a running docker container:

```
docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' forum_security-gate_1
```

### Creating an admin account

- Register an account
- Start a shell session in the running `auth-service` container: `docker exec -it forum_auth-service_1 sh`
- Open the inspector: `./inspector`
- Set the users role to admin: `set-role [user id] admin`

Example:
```
docker exec -it forum_auth-service_1 sh
# ./inspector
No previous history.
main >> set-role 1 admin
The server responded with: ()
```

## Links to docker

- [forum_controller](https://hub.docker.com/r/barskern/forum_controller/)
- [forum_security-gate](https://hub.docker.com/r/barskern/forum_security-gate/)
- [forum_auth-service](https://hub.docker.com/r/barskern/forum_auth-service/)
