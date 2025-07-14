# maven-central-deploy-test
Test deployment to Maven Central with the new Maven plugin, central-publishing-maven-plugin.
I was having some trouble getting the new plugin to work, so I created this repository to test it out.

## Usage
1. Create a namespace to deploy to at https://central.sonatype.com/, if you don't have one already.
2. Create an authentication token in your account, export the username as environment variable, matching those in `settings.xml`:
   ```bash
   export USERNAME=your-username
   export PASSWD=your-password
   ```
3. Import your private GPG key into your local keyring, if you haven't done so already:
   ```bash
   gpg --import your-private-key.asc
   ```
4. Specify the GPG pass phrase to the maven-gpg-plugin (i.e. as the environment variable `MAVEN_GPG_PASSPHRASE`):
   ```bash
   export MAVEN_GPG_PASSPHRASE=your-passphrase
   ```
5. Run the Maven command to deploy:
   ```bash
    mvn deploy --settings settings.xml
    ```
6. If all works well, you should see the artifacts in you deployments in the Central Portal. The maven plugin is not configured to automatically deploy, so it's easy to simply drop the deployment, after a test, thus avoiding pollution of Maven Central.


