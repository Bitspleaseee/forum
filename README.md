# Secure software design

The aim of this project is to create a forum which is mostly secure using the techniques learned in IMT3501.

## Installing and running

This project is configured to run as multiple docker containers. By running the following command you will start up all the required services.

```
docker-compose up
```

Find the IP of the `security-gate` using `docker inspect forum_security-gate_1`, and go to `http://<security-gate-ip>/index.html`.


## Group members

| Name       | Email                 |
| ---------- | --------------------- |
| Eivind     | eivind@aunebakk.no    |
| Uran       | uhajzeraj@hotmail.com |
| Knut       | kgrstad@gmail.com     |
| Yngve      | yjhestem@stud.ntnu.no |
| Ole Martin | barskern@outlook.com  |
