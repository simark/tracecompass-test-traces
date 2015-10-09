Trace Compass Test Traces
=========================

This tree contains a set of CTF test traces, primarily for use in Trace Compass.

To build the package and install it in your local Maven repo, simply isssue

    mvn clean install

You can also use the `deploy` target to populate both a standard Maven repo and
a p2 update site. The `-Dmaven-deploy-destination` and `-Dp2-deploy-destination`
properties can be used to specify their respective deploy locations.
For example:

    mvn clean deploy -Dmaven-deploy-destination=file:///var/www/traces/maven -Dp2-deploy-destination=/var/www/traces/repository

(Note that the first property needs a `file:///` scheme, but the second does not.) 

You can then point depending projects to these locations.


Adding a new CTF test trace
---------------------------

The modules follow the
[Maven standard directory layout](https://maven.apache.org/guides/introduction/introduction-to-the-standard-directory-layout.html).

To add a new CTF test trace, add it to the `ctf/src/main/resources` directory.
Make sure it is not archived or anything, as this will be exposed as-is to the
users.

Then update the `ctf/src/main/java/.../CtfTestTrace.java` file accordingly to
include the new trace.

Finally, bump the project's minor version (1.1 -> 1.2) in the main pom.xml and
related `<parent>` blocks.
