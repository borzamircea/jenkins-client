# jenkins-client

A Java client for the Jenkins API

## Getting Started

To get started add the following dependency to your project

```xml
<dependency>
  <groupId>com.offbytwo.jenkins</groupId>
  <artifactId>jenkins-client</artifactId>
  <version>0.3.1</version>
</dependency>
```

## Usage

The `com.offbytwo.jenkins.JenkinsServer` class provides the main entry
point into the API. You can create a reference to the Jenkins server
given its location and (optionally) a username and password/token.

```java
JenkinsServer jenkins = new JenkinsServer(new URI("http://localhost:8080/jenkins"), "admin", "password")
```

At the top level you can access all of the currently defined
jobs. This returns a map of job names (in lower case) to jobs.

```java
Map<String, Job> jobs = jenkins.getJobs()
```

The Job class provides only summary information (name and url). You can retrieve details as follows

```java
JobWithDetails job = jobs.get("My Job").details()
```

The `JobWithDetails` class provides you with access to the list of
builds (and related information such as the first, last, successful,
etc) and upstream and downstream projects.

## Running Tests
To run only unit tests without invoking the integration tests use the following command:

```
mvn clean install -DskipITs
```


## Running Integration Tests
To run integration tests simply start 

```
mvn clean install
```

## Details about Releases

You can find details about the different releases in the [Release Notes](https://github.com/RisingOak/jenkins-client/blob/master/ReleaseNotes.md).

## License

Copyright (C) 2013, Rising Oak LLC.

Distributed under the MIT license: http://opensource.org/licenses/MIT
