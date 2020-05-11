# lcogt-pom
This parent POM is used across different projects at LCO including
[Site Software](https://github.com/LCOGT/site-software),
the [Site Software Control Interface](https://github.com/LCOGT/site-software-control-interface),
and the [Reduction Service](http://git.lco.gtn/projects/SIT/repos/reduction-service/browse).

# Manual build

    mvn clean install

# Deploy
Jenkins will automatically deploy this POM to Nexus when the follow tasks have
been completed:
- a version has been set in the pom.xml
- this version has also been used to create an annotated git tag and pushed

Make sure to update the version of any projects that use this POM.
