# How to Remotely Debug Java Applications on Cloud Foundry
### PROCEDURE
1. Enable the `JBP_CONFIG_DEBUG` environment variable, this can be done by editing application manifest.yml or invoking the _**"cf set-env"**_ command. In this article, we use application manifest as an example.
```yaml
---
applications:
- name: <APP_NAME>
 memory: 512M
 instances: 1
 path: path/java-app.war
 env:
   JBP_CONFIG_DEBUG: '{enabled: true}'
```
2. Use __*"cf push"*__ to deploy the Java application to PCF or Pivotal Web Services.

3. Set up the SSH tunnel for the debug framework via JDWP. 

>__*cf ssh -N -T -L 8000:localhost:8000 <APP_NAME>*__

Once the SSH tunnel has been created, Eclipse/STS should connect to the localhost:8000 for debug access. Please refer to the detailed instructions in the Java Buildpack Debug Framework. 





