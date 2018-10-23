## Migrating the ``oxygen-sample-webapp`` project to use the new WebAuthor speciffic artifacts

### Using ``web-author-component`` artifact instead of ``oxygen-webapp`` in module ``oxygen-sample-webapp``


Remove the old ``oxygen-webapp`` dependency
    <dependency>
      <groupId>com.oxygenxml</groupId>
      <artifactId>oxygen-webapp</artifactId>
      <version>${oxygen.sdk.version}</version>
      <type>war</type>
      <exclusions>
        <exclusion>
          <groupId>*</groupId>
          <artifactId>*</artifactId>
        </exclusion>
      </exclusions>
    </dependency>

    <dependency>
      <groupId>com.oxygenxml</groupId>
      <artifactId>oxygen-webapp</artifactId>
      <version>${oxygen.sdk.version}</version>
      <classifier>classes</classifier>
      <exclusions>
        <exclusion>
          <groupId>com.oxygenxml</groupId>
          <artifactId>frameworks</artifactId>
        </exclusion>
      </exclusions>
    </dependency>

Add a dependency for the ``web-author-component``

    <dependency>
      <groupId>com.oxygenxml</groupId>
      <artifactId>web-author-component</artifactId>
      <version>${oxygen.sdk.version}</version>
      <type>war</type>
    </dependency>


Replace the ``oxygen-webapp`` overlay configuration:
```
<overlay>
  <groupId>com.oxygenxml</groupId>
  <artifactId>oxygen-webapp</artifactId>
  <excludes>
    <exclude>WEB-INF/frameworks.zip</exclude>
    <exclude>WEB-INF/options.zip</exclude>
    <exclude>WEB-INF/plugins.zip</exclude>
  </excludes>
</overlay>
````

with new ``web-author-component`` overlay
```
<overlay>
  <groupId>com.oxygenxml</groupId>
  <artifactId>web-author-component</artifactId>
</overlay>
```

### Using the new ``web-author-frameworks`` artifact instead of ``frameworks`` in ``bundle-frameworks`` module

Replace the ``bundle-frameworks`` dependency
```
  <dependency>
    <groupId>com.oxygenxml</groupId>
    <artifactId>frameworks</artifactId>
    <version>${oxygen.sdk.version}</version>
    <type>zip</type>
    <scope>provided</scope>
  </dependency>
```
with the new one
```
    <dependency>
      <artifactId>web-author-frameworks</artifactId>
      <groupId>com.oxygenxml</groupId>
      <version>${oxygen.sdk.version}</version>
      <type>zip</type>
      <scope>provided</scope>
    </dependency>
```

Change the `copy-frameworks` maven-dependency-plugin configuration to use the new artifact
