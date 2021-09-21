[//]: # (title: Qodana JVM)

[![official project](https://jb.gg/badges/official-flat-square.svg)](https://confluence.jetbrains.com/display/ALL/JetBrains+on+GitHub)

<var name="linter" value="Qodana JVM"/>

%linter% is based on [IntelliJ IDEA Ultimate](https://www.jetbrains.com/idea/) and provides static analysis for Java and Kotlin for Server Side projects, and related frameworks and technologies.

## Try it now

### Analyse a project locally

To start, pull the image from Docker Hub (only necessary to get the latest version):

<var name="docker-image" value="jetbrains/qodana-jvm"/>

<code style="block" lang="shell">
  docker pull %docker-image%
</code>

and run the analysis locally:

```shell
docker run --rm -it -v <source-directory>/:/data/project/ \ 
  -p 8080:8080 %docker-image% --show-report
```

with `source-directory` pointing to the root of your project.

Check the results in your browser at [`http://localhost:8080`](http://localhost:8080).

> For details on running Qodana in Docker, see the [Docker guide](docker-images.md). 

## Next steps

- <a href="qodana-intellij-docker-readme.md">Configure %linter% Docker image</a>
- <a href="qodana-intellij-github-action.md">Run %linter% on GitHub</a>
- <a href="qodana-intellij-github-application.md">Run %linter% as a GitHub App</a>
- <a href="service.md">Use %linter% as a Service</a>
- <a href="ci.md">Extend your CI/CD with %linter% plugins</a>