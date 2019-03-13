Tags: kubernetes, lab-notes, migrating-odk-to-k8s, odk

# Lab Notes: Migrating ODK Aggregate from Fargate to Azure Kubernetes Services (part 2)

*I'm working on deploying an Aggregate 2.0 instance to Kubernetes in the cleanest possible way, and documenting my progress in these lab notes.*

## More Config Tweaks, yay

So the good news is: my [PR got accepted](https://github.com/opendatakit/aggregate/pull/439)! The bad news is: I still need to do more configuration work. 😞

The best way in k8s to configure Pods is using [ConfigMaps](https://kubernetes.io/docs/tasks/configure-pod-container/configure-pod-configmap/) or [Secrets](https://kubernetes.io/docs/concepts/configuration/secret/). With both ConfigMaps and Secrets, it's possible to bind mount the contents of a key/value pair into an appropriately named file in a directory on the container (or inject them as environment variables). This will allow me to set a `security.properties` value in a ConfigMap and mount it into the appropriate spot for Aggregate.

Unfortunately, it's not possible to mount individual *files* into existing directories, so it's not feasible to simply mount a file such as "security.properties" into ODK's configuration directory. 

This means I needed to tweak the [Docker `entrypoint.sh` file a bit](https://github.com/opendatakit/aggregate/compare/master...brettneese:docker-entrypoint-tweaks) to create symbolic links from a configuration directory into the appropriate web app directory in ODK. 

This new code allows the bind-mounting of config files to `/etc/config/`. Any environmental variables that are set will override the values in those files, as was already the case.

I still need to filter out the DB password and work on docs, but combined with the previous PR, it's a great start to much improving the Aggregate configuration experience using Docker.

The great part about this is that it _also_ works without k8s, using a simple bind mount passed to Docker, such as:

```docker run -e DB_USERNAME=brett --mount type=bind,source="$(pwd)"/src/main/resources/jdbc.properties.example,target=/etc/config/jdbc.properties,readonly aggregate:v2.0.1-3-ge2056912-dirty```

In this case, whatever is in `./src/main/resources/jdbc.properties.example` gets mounted to `/etc/config/jdbc.properties` which is symlinked into `${AGGREGATE_CONF_DIR}/jdbc.properties`, where ODK Aggregate reads it. The DB_USERNAME in this example is also being overriden using environment variables to "brett," instead of whatever is specified in that file. This allows easy rotation in case of leaked secrets.