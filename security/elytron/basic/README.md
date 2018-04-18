# Elytron Basic Auth Sample

This example is identical to JPA, JAX-RS and CDI with Shrinkwrap Example,
with the addition of setting up Elytron.

## Run

You can run it many ways:

* mvn package && java -jar ./target/example-elytron-basic-swarm.jar
* mvn wildfly-swarm:run
* In your IDE run the `org.wildfly.swarm.Swarm` class

## Bug Notice

The elytron fraction currently (2018.5.0-SNAPSHOT) ignores mappings in swarm.elytron.jdbc-realms.KEY.principal-query, e.g. 'attribute-mapping' or 'clear-password-mapper'. See [SWARM-???](https://issues.jboss.org/browse/SWARM-???) for details.

Workaround: Properly setup the elytron fraction as .xml. See an example for this project here in (src/main/resources/standalone.xml.workaround)[src/main/resources/standalone.xml.workaround]. When you rename that file to `src/main/resources/standalone.xml`, and rerun this example application, it will all work.

## Use

http://localhost:8080/

You can see a Basic access authentication dialog for username/password.

Input `Penny/password` to get a list of all Employees which is permitted only to users in the 'admin' role.
Restart a browser and input `Sheldon/password` ('user' role) and get an empty list of Employees.
Finally, restart a browser and input `Amy/password` ('guest' role) and get a 'Forbidden' response.
