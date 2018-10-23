## Migrating the Oxygen XML SDK sample project to use the ``com.oxygenxml:web-author-component`` artifacts

## In the root pom.xml:
Declare the Web Author Component version as a property in the  ``<properties>`` element like:
 ``<web.author.component.version>[Placeholder]</web.author.component.version>``, where ``[Placeholder]`` must be replace with the actual version like 20.1.1



## In module ``oxygen-sample-webapp``

### Replace ``com.oxygenxml:oxygen-webapp`` artifacts with ``com.oxygenxml:web-author-component``
Remove the old ``com.oxygenxml:oxygen-webapp:war`` dependency:
```
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
```

Remove the old ``com.oxygenxml:oxygen-webapp:classes`` dependency:
```
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
```

Add the new ``web-author-component`` dependency:
```
    <dependency>
      <groupId>com.oxygenxml</groupId>
      <artifactId>web-author-component</artifactId>
      <version>${web.author.component.version}</version>
      <type>war</type>
    </dependency>
```

### Update ``maven-war-plugin`` section
Replace the ``oxygen-webapp`` overlay configuration:
```
<overlay>
  <groupId>com.oxygenxml</groupId>
  <artifactId>oxygen-webapp</artifactId>
  <excludes>
    ...
  </excludes>
</overlay>
```

with new ``web-author-component`` overlay
```
<overlay>
  <groupId>com.oxygenxml</groupId>
  <artifactId>web-author-component</artifactId>
</overlay>
```

### Mark the SDK dependency as `provided`
Declare ``com.oxygenxml:oxygen-sdk`` as provided to override parent's configuration by adding:
```
    <dependency>
      <groupId>com.oxygenxml</groupId>
      <artifactId>oxygen-sdk</artifactId>
      <version>${oxygen.sdk.version}</version>
      <scope>provided</scope>
    </dependency>
```



## In module ``bundle-frameworks``
### Replace ``com.oxygenxml:frameworks`` artifact with ``com.oxygenxml:web-author-frameworks``:
Replace the ``bundle-frameworks`` dependency:
```
  <dependency>
    <groupId>com.oxygenxml</groupId>
    <artifactId>frameworks</artifactId>
    <version>${oxygen.sdk.version}</version>
    <type>zip</type>
    <scope>provided</scope>
  </dependency>
```
with the new one:
```
    <dependency>
      <groupId>com.oxygenxml</groupId>
      <artifactId>web-author-frameworks</artifactId>
      <version>${web.author.component.version}</version>
      <type>zip</type>
      <scope>provided</scope>
    </dependency>
    
```

Update the ``artifactId`` from the configuration of the  ``maven-dependency-plugin`` to use the new frameworks artefact, "``com.oxygenxml::web-author-frameworks``": 
Replace
```
                  <artifactId>frameworks</artifactId>
```
with
```
                  <artifactId>web-author-frameworks</artifactId>
```
