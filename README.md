# ATI Parent

This is the parent for all ATI projects.

## Version number policy

This project uses a single number for its version. The next release will have
the next number in order as its version.

## Preparing for making releases

To make a release there are a couple of things that you need to set up manually.

### Set up GPG

To be able to sign the release artifacts you need to install GPG on your machine
and create a signing certificate. 

### Configure your settings.xml

You need to add the following configuration to your ```settings.xml``` file:
```
  <servers>
    <server>
      <id>github</id>
      <username>your-github-username</username>
      <password>your-github-password</password>
    </server>
    <server>
      <id>central</id>
      <username>your-maven-central-username</username>
      <password>your-maven-central-password</password>
    </server>
    ...
  </servers>

  <profiles>
    <profile>
      <id>ati-release</id>
      <properties>
        <gpg.passphrase>your-gpg-passphrase</gpg.passphrase>
      </properties>
    </profile>
    ...
  </profiles>

```

## Making a release

Run these commands in sequence, answering the questions about version numbers
and tag name. The default values should be fine in most cases.

```
mvn clean verify
mvn release:prepare
mvn release:perform
```

Next log in to Maven Central Portal to finish the job by following
[these instructions](https://central.sonatype.org/publish/publish-portal-guide/)
