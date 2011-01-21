org.clojure parent POMs
========================================

This project defines a parent Maven Project Object Model (POM) for
projects contributed to Clojure and built at
[build.clojure.org](http://build.clojure.org).


What does this POM do?
========================================

The pom.xml file of this project defines a common configuration
baseline for libraries contributed to Clojure, including:

* Parent POM: org.sonatype.oss:oss-parent
  * enables automated releases to the Sonatype open-source Maven repository, and then to the Maven central repository
* Build properties
  * `clojure.version` defined to be the most recent release of Clojure
    * This may be an alpha or beta release
    * This may be changed on the Maven command line to test with different versions
  * `clojure.warnOnReflection` sets the `*warn-on-reflection*` flag during compilation
    * Defaults to false
    * This may be changed on the Maven command line to test with `*warn-on-reflection*` true
  * `project.build.sourceEncoding` set to UTF-8
* License set to EPL 1.0
* Build plugin configuration
  * build-helper-maven-plugin
    * Adds src/main/clojure to the source and resource directories for the project
    * Adds src/test/clojure to the test source and test resource directories for the project
    * Ensures sources will be recognized by other plugins and copied to the output JAR
  * maven-compiler-plugin
    * Sets Java source and target version to 1.5
    * Sets Java source file encoding to UTF-8
  * maven-release-plugin
    * Prevents tags and other changes from being pushed to Git when a release build fails
  * com.theoryinpractise:clojure-maven-plugin
    * AOT-compiles all .clj sources as a syntax check
    * Does *not* include any AOT-compiled .class files in the output JAR
    * Runs tests defined with clojure.test
    * Does *not* AOT-compile test .clj sources
* Build profiles
  * Default profile
    * Adds dependency on a Clojure release defined by the `clojure.version` property
  * "local-clojure-jar" profile
    * Adds "system" dependency on a Clojure JAR anywhere on the local filesystem
    * Enabled by setting the `clojure.jar` property on the command line
      * Must be set to the absolute path to the Clojure JAR file


What do contrib projects need to do?
========================================

Unless they have special build requirements such as `gen-class`,
contrib projects should only require three things:

* Clojure sources in `src/main/clojure/`
* Test sources using clojure.test in `src/test/clojure/`
* A pom.xml file that looks like example-project-pom.xml
