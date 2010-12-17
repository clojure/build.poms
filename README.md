# org.clojure parent POMs

This project defines a parent POM for projects contributed to Clojure and
built at [build.clojure.org](http://build.clojure.org). 

Clojure-contrib projects should have a `pom.xml` file with a `parent`
declaration like this:

    <parent>
      <groupId>org.clojure</groupId>
      <artifactId>pom.contrib</artifactId>
      <version>${version}</version>
    </parent>

where `${version}` is the most recent release version of pom.contrib.
