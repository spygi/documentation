## Philosophy
- Inheritance e.g. in POMs
- Convention over configuration e.g. file structure has to be src and test, default bindings for phases
- Everything is a plugin, see here [available plugins](https://maven.apache.org/plugins/)

## Glossary:
- Build lifecycles: the default ones are clean, default, site 
- Each lifecycle contains phases, e.g. default containts validate, compile, test, package, verify, install, deploy [among others](https://maven.apache.org/guides/introduction/introduction-to-the-lifecycle.html#Lifecycle_Reference).
- Each phase is made of plugin goals: "A plugin goal represents a specific task (finer than a build phase)".
A goal can belong to 0..N phases (if it belongs to 0 phases it can be invoked directly)
A phase can contain 0..N goals (if it contains 0 goals, the phase won't be executed)
Hyphenated processes like process- pre- post- are not meant to be run individually.

For example 
mvn <phase> <plugin:goal>
run all the phases up to phase in order and then runs the plugin:goal

There are 2 ways to add goals to phases:
- By setting the <packaging> property of the project, see here for its [binding](https://maven.apache.org/ref/3.6.0/maven-core/default-bindings.html)
- By adding plugins and their goals

To check which goals are in a phase mvn help:describe -Dcmd=PHASE or this mvn fr.jcgay.maven.plugins:buildplan-maven-plugin:list|-plugin|-phase, 
