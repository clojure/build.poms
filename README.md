# org.clojure parent POMs

This project and its modules define various parent POMs to be used by
build processes at [build.clojure.org](http://build.clojure.org). Here is a
list of the available POMs, each of which defines the previous as its parent:

- `org.clojure:pom.oss-deploy` ropes in the `org.sonatype.oss:oss-parent` POM,
enabling the deployment to Sonatype's OSS repositories (and handily setting
a variety of other common basics, like source file encoding, attaching a source
artifact to deployments, etc).
- `org.clojure:pom.baseline` adds:
    - a `org.clojure:clojure` dependency (with its version parameterized
via `clojure.version`, currently defaulting to 1.2.0)
    - [clojure-maven-plugin](http://github.com/talios/clojure-maven-plugin) with
sane defaults
    - specifies 1.5 source and target for `maven-compiler-plugin` (for those
contrib projects that do have Java sources; also is used by various IDEs as
a hint about which JDK to configure for an imported project)
- `org.clojure:pom.contrib`, which currently defines nothing itself, but which
should be the parent POM of all contrib projects going forward.  This is where
we could add various enforcer configurations to verify POM characteristics
we care about.