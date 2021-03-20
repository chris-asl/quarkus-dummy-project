# Quarkus dummy project

Initial Quarkus project to demonstrate build image failure with Kaniko.

Building locally with a Docker daemon available for testing the build  

```bash
docker run \
  -v "/path/to/quarkus-dummy-project":/workspace \
  gcr.io/kaniko-project/executor:v1.5.1-debug \
  --dockerfile "src/main/docker/Dockerfile.jvm" \
  --context dir:///workspace/ \
  --no-push
```

This fails with  
```
...
INFO[0036] COPY --chown=1001 target/quarkus-app/lib/ /deployments/lib/ 
error building image: error building stage: failed to execute command: getting user group from chown: user: unknown user 1001
```

