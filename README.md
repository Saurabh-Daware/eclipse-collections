# Eclipse Collections

[![][travis img]][travis]
[![][maven img]][maven]
[![][license-epl img]][license-epl]
[![][license-edl img]][license-edl]

Eclipse Collections is a collections framework for Java. It has JDK-compatible List, Set and Map implementations with a rich API and set of utility classes that work with any JDK compatible Collections, Arrays, Maps or Strings. The iteration protocol was inspired by the Smalltalk collection framework.

## Quick Example
Eclipse Collections puts iteration methods on the container types. Lambdas are simulated using anonymous inner classes. Here's a code example that demonstrates the usual style of programming with Eclipse Collections.

```java
MutableList<Person> people = FastList.newListWith(person1, person2, person3);
MutableList<String> sortedLastNames = people.collect(Person.TO_LAST_NAME).sortThis();
System.out.println("Comma separated, sorted last names: " + sortedLastNames.makeString());
```

Person.TO_LAST_NAME is defined as a constant Function in the Person class.

```java
public static final Function<Person, String> TO_LAST_NAME = new Function<Person, String>()
{
    public String valueOf(Person person)
    {
        return person.lastName;
    }
};

```
In Java 8, the Function can be replaced with a lambda:

```java
MutableList<String> sortedLastNames = people.collect(person -> person.getLastName()).sortThis();
```

Or, a method reference:

```java
MutableList<String> sortedLastNames = people.collect(Person::getLastName).sortThis();
```

## Why Eclipse Collections?
* Improves readability and reduces duplication of iteration code (enforces DRY/OAOO)
* Implements several, high-level iteration patterns (select, reject, collect, inject into, etc.) on "humane" container interfaces which are extensions of the JDK interfaces
* Provides a consistent mechanism for iterating over Collections, Arrays, Maps, and Strings
* Provides replacements for ArrayList, HashSet, and HashMap optimized for performance and memory usage
* Performs more "behind-the-scene" optimizations in utility classes
* Encapsulates a lot of the structural complexity of parallel iteration and lazy evaluation
* Adds new containers including Bag, Interval, Multimap, BiMap, and immutable versions of all types
* Has been under active development since 2005 and is a mature library

## Acquiring Eclipse Collections

### Maven
```xml
<dependency>
  <groupId>org.eclipse.collections</groupId>
  <artifactId>eclipse-collections-api</artifactId>
  <version>7.0.0</version>
</dependency>

<dependency>
  <groupId>org.eclipse.collections</groupId>
  <artifactId>eclipse-collections</artifactId>
  <version>7.0.0</version>
</dependency>

<dependency>
  <groupId>org.eclipse.collections</groupId>
  <artifactId>eclipse-collections-testutils</artifactId>
  <version>7.0.0</version>
  <scope>test</scope>
</dependency>

<dependency>
  <groupId>org.eclipse.collections</groupId>
  <artifactId>eclipse-collections-forkjoin</artifactId>
  <version>7.0.0</version>
</dependency>
```

### Gradle

```groovy
compile 'org.eclipse.collections:eclipse-collections-api:7.0.0'
compile 'org.eclipse.collections:eclipse-collections:7.0.0'
testCompile 'org.eclipse.collections:eclipse-collections-testutils:7.0.0'
compile 'org.eclipse.collections:eclipse-collections-forkjoin:7.0.0'
```

### Ivy

```xml
<dependency org="org.eclipse.collections" name="eclipse-collections-api" rev="7.0.0" />
<dependency org="org.eclipse.collections" name="eclipse-collections" rev="7.0.0" />
<dependency org="org.eclipse.collections" name="eclipse-collections-testutils" rev="7.0.0" />
<dependency org="org.eclipse.collections" name="eclipse-collections-forkjoin" rev="7.0.0"/>
```

[travis]:https://travis-ci.org/eclipse/eclipse-collections
[travis img]:https://travis-ci.org/eclipse/eclipse-collections.svg?branch=master

[maven]:http://search.maven.org/#search|gav|1|g:"org.eclipse.collections"%20AND%20a:"eclipse-collections"
[maven img]:https://maven-badges.herokuapp.com/maven-central/org.eclipse.collections/eclipse-collections/badge.svg

[license-epl]:LICENSE-EPL-1.0.txt
[license-epl img]:https://img.shields.io/badge/License-EPL-blue.svg

[license-edl]:LICENSE-EDL-1.0.txt
[license-edl img]:https://img.shields.io/badge/License-EDL-blue.svg
