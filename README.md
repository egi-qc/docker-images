
Docker images used for deploying UMD software verifications.

Description
===========

The verification infrastructure relies on a Jenkins CI service, deployed as a Docker container:
```
	docker run -v /var/run/docker.sock:/run/docker.sock -v $(which docker):/bin/docker -p 8000:8080 -p 50000:50000 orviz/umd-jenkins
```

that triggers UMD product verifications by using Jenkins Docker plugin.
