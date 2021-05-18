# khipster

This application was generated using JHipster 6.10.5, you can find documentation and help at [https://www.jhipster.tech/documentation-archive/v6.10.5](https://www.jhipster.tech/documentation-archive/v6.10.5).

## Development

Before you can build this project, you must install and configure the following dependencies on your machine:

1. [Node.js][]: We use Node to run a development web server and build the project.
   Depending on your system, you can install Node either from source or as a pre-packaged bundle.

After installing Node, you should be able to run the following command to install development tools.
You will only need to run this command when dependencies change in [package.json](package.json).

```
npm install
```

We use npm scripts and [Webpack][] as our build system.

Run the following commands in two separate terminals to create a blissful development experience where your browser
auto-refreshes when files change on your hard drive.

```


./gradlew -x webpack

npm start
```

Npm is also used to manage CSS and JavaScript dependencies used in this application. You can upgrade dependencies by
specifying a newer version in [package.json](package.json). You can also run `npm update` and `npm install` to manage dependencies.
Add the `help` flag on any command to see how you can use it. For example, `npm help update`.

The `npm run` command will list all of the scripts available to run for this project.

### PWA Support

JHipster ships with PWA (Progressive Web App) support, and it's turned off by default. One of the main components of a PWA is a service worker.

The service worker initialization code is commented out by default. To enable it, uncomment the following code in `src/main/webapp/index.html`:

```html
<script>
  if ('serviceWorker' in navigator) {
    navigator.serviceWorker.register('./service-worker.js').then(function () {
      console.log('Service Worker Registered');
    });
  }
</script>
```

Note: [Workbox](https://developers.google.com/web/tools/workbox/) powers JHipster's service worker. It dynamically generates the `service-worker.js` file.

### Managing dependencies

For example, to add [Leaflet][] library as a runtime dependency of your application, you would run following command:

```
npm install --save --save-exact leaflet
```

To benefit from TypeScript type definitions from [DefinitelyTyped][] repository in development, you would run following command:

```
npm install --save-dev --save-exact @types/leaflet
```

Then you would import the JS and CSS files specified in library's installation instructions so that [Webpack][] knows about them:
Note: There are still a few other things remaining to do for Leaflet that we won't detail here.

For further instructions on how to develop with JHipster, have a look at [Using JHipster in development][].

### Doing API-First development using openapi-generator

[OpenAPI-Generator]() is configured for this application. You can generate API code from the `src/main/resources/swagger/api.yml` definition file by running:

```bash
./gradlew openApiGenerate
```

Then implements the generated delegate classes with `@Service` classes.

To edit the `api.yml` definition file, you can use a tool such as [Swagger-Editor](). Start a local instance of the swagger-editor using docker by running: `docker-compose -f src/main/docker/swagger-editor.yml up -d`. The editor will then be reachable at [http://localhost:7742](http://localhost:7742).

Refer to [Doing API-First development][] for more details.

## Building for production

### Packaging as jar

To build the final jar and optimize the khipster application for production, run:

```


./gradlew -Pprod clean bootJar

```

This will concatenate and minify the client CSS and JavaScript files. It will also modify `index.html` so it references these new files.
To ensure everything worked, run:

```


java -jar build/libs/*.jar

```

Then navigate to [http://localhost:8080](http://localhost:8080) in your browser.

Refer to [Using JHipster in production][] for more details.

### Packaging as war

To package your application as a war in order to deploy it to an application server, run:

```


./gradlew -Pprod -Pwar clean bootWar

```

## Testing

To launch your application's tests, run:

```
./gradlew test integrationTest jacocoTestReport
```

### Client tests

Unit tests are run by [Jest][] and written with [Jasmine][]. They're located in [src/test/javascript/](src/test/javascript/) and can be run with:

```
npm test
```

For more information, refer to the [Running tests page][].

### Code quality

Sonar is used to analyse code quality. You can start a local Sonar server (accessible on http://localhost:9001) with:

```
docker-compose -f src/main/docker/sonar.yml up -d
```

You can run a Sonar analysis with using the [sonar-scanner](https://docs.sonarqube.org/display/SCAN/Analyzing+with+SonarQube+Scanner) or by using the gradle plugin.

Then, run a Sonar analysis:

```
./gradlew -Pprod clean check jacocoTestReport sonarqube
```

For more information, refer to the [Code quality page][].

## Using Docker to simplify development (optional)

You can use Docker to improve your JHipster development experience. A number of docker-compose configuration are available in the [src/main/docker](src/main/docker) folder to launch required third party services.

For example, to start a postgresql database in a docker container, run:

```
docker-compose -f src/main/docker/postgresql.yml up -d
```

To stop it and remove the container, run:

```
docker-compose -f src/main/docker/postgresql.yml down
```

You can also fully dockerize your application and all the services that it depends on.
To achieve this, first build a docker image of your app by running:

```
./gradlew bootJar -Pprod jibDockerBuild
```

Then run:

```
docker-compose -f src/main/docker/app.yml up -d
```

For more information refer to [Using Docker and Docker-Compose][], this page also contains information on the docker-compose sub-generator (`jhipster docker-compose`), which is able to generate docker configurations for one or several JHipster applications.

## Continuous Integration (optional)

To configure CI for your project, run the ci-cd sub-generator (`jhipster ci-cd`), this will let you generate configuration files for a number of Continuous Integration systems. Consult the [Setting up Continuous Integration][] page for more information.

[jhipster homepage and latest documentation]: https://www.jhipster.tech
[jhipster 6.10.5 archive]: https://www.jhipster.tech/documentation-archive/v6.10.5
[using jhipster in development]: https://www.jhipster.tech/documentation-archive/v6.10.5/development/
[using docker and docker-compose]: https://www.jhipster.tech/documentation-archive/v6.10.5/docker-compose
[using jhipster in production]: https://www.jhipster.tech/documentation-archive/v6.10.5/production/
[running tests page]: https://www.jhipster.tech/documentation-archive/v6.10.5/running-tests/
[code quality page]: https://www.jhipster.tech/documentation-archive/v6.10.5/code-quality/
[setting up continuous integration]: https://www.jhipster.tech/documentation-archive/v6.10.5/setting-up-ci/
[node.js]: https://nodejs.org/
[yarn]: https://yarnpkg.org/
[webpack]: https://webpack.github.io/
[angular cli]: https://cli.angular.io/
[browsersync]: https://www.browsersync.io/
[jest]: https://facebook.github.io/jest/
[jasmine]: https://jasmine.github.io/2.0/introduction.html
[protractor]: https://angular.github.io/protractor/
[leaflet]: https://leafletjs.com/
[definitelytyped]: https://definitelytyped.org/
[openapi-generator]: https://openapi-generator.tech
[swagger-editor]: https://editor.swagger.io
[doing api-first development]: https://www.jhipster.tech/documentation-archive/v6.10.5/doing-api-first-development/

https://news.ycombinator.com/item?id=27183076

Kotlin is a lot more 'proprietary'. For example, quite a few details about how kotlinc works internally is managed by having kotlin-genned class files have a @Metadata annotation that contain a binary blob (a byte array, legal in annotations) with data that is, as far as I know, not according to any publically available spec. There are also various hardcoded types. This is all quite pragmatic, but it also means that without IDEA, kotlin dies immediately. Pragmatically speaking, a minor niggle. But perhaps you find this lack of openness more important than 'minor niggle'.

Kotlin seems to be marketed (both by the community and idea) as java with some minor warts removed. But, what does that mean? Is kotlin supposed to remain 'extremely easy to pick up if you already know java' and 'so close to it, you can interop java and kotlin code with relatively little headache' for the foreseeable future (in which case I foresee some problems I will explain below), or was that mostly just a bootstrap scenario; a way to get a bunch of existing java programmers on board quickly, and give them the ability to transfer their codebase from java to kotlin step by step (by using the interop / double-compile feature)? If that's what it is, then I too foresee some issues in the future. I get the feeling that kotlin folks sort of think it is both, but they are mutually exclusive, so that makes no sense. If you ask someone more familiar with kotlin than I am to explain what kotlin is and/or why the following two arguments do not apply or are properly mitigated, make sure you first establish with them what kotlin's supposed to be.

If kotlin is supposed to be 'java but better' forever
That's a real problem. I can best explain it using a new feature.

All of kotlin's features fall in one of 3 categories:

It is the kotlin take on a java feature that existed when the kotlin take was designed. Therefore, the kotlin variant takes into account what's familiar to java programmers and either follows it closely, or if it deviates, it did so for presumably good reasons (switching type and name around and making semis optional don't strike me as good reasons, but this post is long enough as is, and there's a lot of 'personal preference' peppered into that one, so I'll leave that one out of this for now).

It is the kotlin take on a feature that java straight up just does not have and still does not have. They've clearly gone their own way and decided to add it because it's important.

The problem category: It used to be like the second category (feature java doesn't have), but java has it now. If kotlin is very very lucky, the way java does it, and the way kotlin does it, are similar enough that it all continues to make sense (the learning curve for a java coder to switch to kotlin is not dampened by this), for example if the java impl and the kotlin impl closely align, that's fine. But what if they don't?

Here's the point: Over time, more and more kotlin features are of the third category, and this means that kotlin's 'java but better' take is doomed.

Here's an example: instanceof pattern matching. This feature did not exist, and wasn't even on the radar (no JEP, no public posts on e.g. amber-dev@openjdk.net) when kotlin was released.

The problem it attempts to solve is that you sometimes want to first check if some expression is instanceof some type, and then, if it is, operate on that data, using the fact that it is that instance.

In original java (up to java 14), it looks like:

if (x instanceof String) {
    String y = (String) x;
    System.out.println(y.toLowerCase());
}
in kotlin it looks roughly like:

if (x instanceof String) {
  // in kotlin, x is now assumed to be a string!
    System.out.println(x.toLowerCase());
}
But in java16+, it looks like:

if (x instanceof String y) {
    System.out.println(y.toLowerCase());
}
Now, both java and kotlin cater to this use case, they cater to it in a different way, and I'm pretty sure that if I could smack a giant reset button and design kotlin all over again and release it today into public beta, then kotlin would have followed in java's shoes. Especially considering that the java version is in many ways far more powerful than kotlins: You can do more than just 'check type' with this syntax (you can also 'deconstruct' value types), you don't NEED a block, as in, this works too:

if (!(x instanceof String y)) return;
System.out.println(y.toLowerCase());
and in general the next few releases of java are expanding on this principle, adding lots of pattern matching.

Kotlin now has to make a choice:

Break everything, kill the old way it works, and follow in java's footsteps. This is disastrous (and extremely unlikely to occur). It would break everyone's code, and it means kotlin is permanently dragged down considerably, as this won't be the last time kotlin clashes with some new java feature. Surely you wouldn't want a language that breaks the world every year or two.

Just stick with the kotlin style. That means the argument of 'it is easy to transition from java to kotlin' has gotten a little weaker, and every new java feature released will weaken it more.

Kotlin keeps what it had, but also adds this new syntax. That sounds great, but it means kotlin gains feature cruft twice as fast as java does, and thus over time kotlin will become the bloated bizarro mess of too-many-ways-to-do-the-same-thing, inflating learning curves for no benefit.

Some more intellingent but convoluted solution, such as keeping both but setting up a deprecating scheme for the 'old' way. This still means that kotlin is permanently in java's shadow and cannot possibly get out of it.

None of these 4 options seem all that good to me. Which gets us to what I think kotlin is going to do, and the one that seems the least bad: Option 2 - start parting ways with java syntax. That leads us to:

That like-java thing was just a bootstrap solution
That means the clock is now ticking. Java development is not sitting still at all, so in a year or 3, the gap between kotlin and java is going to be wide enough that kotlin perhaps no longer feels like 'just, java, with a few warts removed'. It'll really feel like something completely different.

That's fine, of course, but the success rate of new languages is abysmal. Scala is pretty much dead (in the sense that it got a bunch of hype, twitter switched over to it, held a ton of fun meets for devs, and... scala now has fewer users than back then, going by admittedly known-inprecise measurement tools such as TIOBE, but, you tell me, do you feel scala is really picking up steam)? - Fan/Fantom seems to have gone absolutely nowhere, groovy is dead enough that e.g. gradle is trying to diversify away from it, jruby and jython have pretty much come and gone (again in the sense that they don't seem to have caught fire).

That's no proof that a new language is doomed perse. It's just that this is the default position. Right now kotlin seems to be having its moment in the sun, but it'll get harder as the step to kotlin from java gets harder and harder.

It'll have to stand on its own and can no longer claim all the advantages java and its ecosystem have by default. The implementation of e.g. instanceof in java vs. kotlin is already highlighting why I, personally, think kotlin is probably not going to be better than java: Just about every feature that java has released, and is in the process of releasing (as in, active JEPs and active discussions on the mailing lists) seems vastly more intelligently thought out than any of kotlin's features. Java is trying to figure out smart ways to access CPU-native 80-bit registers, how to have complex value types that nevertheless have the performance and memory benefits of primitives, and a whole new programming paradigm by way of pattern matching.

