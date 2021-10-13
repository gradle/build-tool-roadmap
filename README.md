# Gradle Build Tool roadmap

## About this repository

This repository contains a public roadmap for the Gradle Build Tool project. Major engineering projects are captured as GitHub issues, which only Gradle staff can create or update. You can subscribe to this repository to get updates about the current projects. You can also see a board with status of each item at https://github.com/orgs/gradle/projects/13/views/1. 

Many smaller improvements and bug fixes are made in every Gradle release. See the [issue tracker](https://github.com/gradle/gradle/issues) and release notes for details.

## About the current roadmap

Our main areas of focus for the Gradle Build Tool are performance and ease of use for JVM and Android ecosystems.

### Performance

On performance side, we focus primarily on making [incremental builds](https://docs.gradle.org/current/userguide/more_about_tasks.html#sec:up_to_date_checks) much faster. The goal is to optimize making frequent small changes in the development process. For example, when running a test in Intellij IDEA with "delegate to Gradle" option or when deploying a change to an emulator in Android Studio, the feedback loop should be as fast as possible.

Currently, Gradle's configuration phase adds some overhead in incremental builds which can be very noticeable especially in large builds. This is being addressed by the [configuration cache](https://github.com/gradle/build-tool-roadmap/issues/2) that caches the configuration phase in subsequent builds. 

We are also working on addressing a big point for many teams with long sync times in the IDE through [isolated projects](https://github.com/gradle/build-tool-roadmap/issues/3) work. This project will also make configuration cache much faster in addition to caching mentioned above. 

In Gradle 7.0, we [enabled file system watching by default](https://github.com/gradle/build-tool-roadmap/issues/11) which helps to avoid a lot of I/O operations during incremental builds by storing file system state in memory. We are now working on [using the underlying infrastructure to improve the continous build](https://github.com/gradle/build-tool-roadmap/issues/4) feature.

### Ease of use

As for ease of use, we are working on providing conveniences for common use cases. For example, [declarative test suites](https://github.com/gradle/build-tool-roadmap/issues/6) in the upcoming Gradle 7.3 release will make it easier to add additional test groups like integration or functional tests. Next, we will provide an easier way to [aggregate code quality reports](https://github.com/gradle/build-tool-roadmap/issues/8) from multiple subprojects. In Gradle 7.0, we introduced [version catalog feature preview](https://github.com/gradle/build-tool-roadmap/issues/12) to make it easier to declare external dependency version, especially in multiproject builds. As one of the next steps, we are planning to [make the version catalog stable](https://github.com/gradle/build-tool-roadmap/issues/10).

We are also planning to polish some of the existing APIs and DSLs. Some of the APIs we would like to improve are very widely used so as one of the steps in this direction, we are exploring how we can [evolve APIs](https://github.com/gradle/build-tool-roadmap/issues/5) with fewer breaking changes. 
