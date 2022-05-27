# quinoa-vite-reproducer Project

This is a reproducer project to demonstrate that quinoa is not forwarding on to the vite server for calls to http://localhost:8080 (root) resulting in a Resource not Found message, however http://localhost:8080/index.html does resolve correctly, odd since vite server responds to http://localhost:3000 so unclear why the app is not forwarding to the dev server for root.

When the app is built it all works perfectly, just the dev mode has the issue.

When testing against the default quinoa quickstart, quinoa does indeed work as expected forwarding the request to the dev-server so http://localhost:8080 responds with the Theater app.

This app contains 2 webui directories, by default configured to use the vite failing case, but enable the property to see the 'working' default case.

```
#quarkus.quinoa.ui-dir=src/main/webui_starter
```

## Running the application in dev mode

You can run your application in dev mode that enables live coding using:

```shell script
./mvnw compile quarkus:dev
```

> **_NOTE:_** Quarkus now ships with a Dev UI, which is available in dev mode only at http://localhost:8080/q/dev/.

## Packaging and running the application

The application can be packaged using:

```shell script
./mvnw package
```

It produces the `quarkus-run.jar` file in the `target/quarkus-app/` directory.
Be aware that it’s not an _über-jar_ as the dependencies are copied into the `target/quarkus-app/lib/` directory.

The application is now runnable using `java -jar target/quarkus-app/quarkus-run.jar`.

If you want to build an _über-jar_, execute the following command:

```shell script
./mvnw package -Dquarkus.package.type=uber-jar
```

The application, packaged as an _über-jar_, is now runnable using `java -jar target/*-runner.jar`.

## Creating a native executable

You can create a native executable using:

```shell script
./mvnw package -Pnative
```

Or, if you don't have GraalVM installed, you can run the native executable build in a container using:

```shell script
./mvnw package -Pnative -Dquarkus.native.container-build=true
```

You can then execute your native executable with: `./target/code-with-quarkus-1.0.0-SNAPSHOT-runner`

If you want to learn more about building native executables, please consult https://quarkus.io/guides/maven-tooling.

## Related Guides

- Quinoa ([guide](https://quarkiverse.github.io/quarkiverse-docs/quarkus-quinoa/dev/index.html)): Quinoa is a Quarkus extension which eases the development, the build and serving single page apps or web components (built with NodeJS: React, Angular, Vue, Lit, …) alongside other Quarkus services (REST, GraphQL, Security, Events, ...).

Live code the backend and frontend together with close to no configuration. When enabled in development mode, Quinoa will start the UI live coding server provided by the target framework and forward relevant requests to it. In production mode, Quinoa will run the build and process the generated files to serve them at runtime.

## Provided Code

### Quinoa

This is a tiny webpack app to get started with Quinoa. It generates a quinoa.html page and a script.

[Related guide section...](https://quarkiverse.github.io/quarkiverse-docs/quarkus-quinoa/dev/index.html)
