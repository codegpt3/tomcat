# Tomcat on Amazon Corretto (Amazon Linux 2023)

The Docker Official Image for Tomcat no longer publishes or maintains Amazon Corretto variants. This independent community project keeps Tomcat images based on Amazon Corretto for users who need them. It is not an official Apache Tomcat, Amazon Corretto, or Docker Official Image.

## Published tags

Images are published to the Docker Hub repository configured by `DOCKER_USER` in the publishing workflow (for example, `your-docker-user/tomcat`). Replace `your-docker-user` below with that Docker Hub namespace.

| Tomcat line | JDK tags | JRE tags |
| --- | --- | --- |
| 11.0 | `11.0-jdk17-corretto-al2023`, `11.0-jdk21-corretto-al2023`, `11.0-jdk25-corretto-al2023` | — |
| 10.1 | `10.1-jdk11-corretto-al2023`, `10.1-jdk17-corretto-al2023`, `10.1-jdk21-corretto-al2023`, `10.1-jdk25-corretto-al2023` | — |
| 9.0 | `9.0-jdk8-corretto-al2023`, `9.0-jdk11-corretto-al2023`, `9.0-jdk17-corretto-al2023`, `9.0-jdk21-corretto-al2023`, `9.0-jdk25-corretto-al2023` | `9.0-jre8-corretto-al2023` |

Each published variant also has a full-version tag, such as `9.0.122-jdk8-corretto-al2023`. The full-version tag is created for each Tomcat release; the corresponding `9.0-...`, `10.1-...`, or `11.0-...` tag moves forward when a new release is published. There is no `latest` tag. Only the Corretto variants listed above are published by this project.

The [publishing workflow](.github/workflows/corretto-publish.yml) checks for new Tomcat releases daily and rebuilds and pushes Corretto images when versions change. Manual runs can also force a rebuild. Published images target `linux/amd64` and `linux/arm64`.

## Usage

```console
docker run --rm -p 8888:8080 your-docker-user/tomcat:9.0-jdk17-corretto-al2023
```

Open `http://localhost:8888`. A 404 response is expected until a web application is deployed: Tomcat's example webapps are not enabled by default. To deploy an application, copy its WAR file to `/usr/local/tomcat/webapps/` in a derived image or mount it there.

For image build definitions, see the `corretto-al2023` directories under [9.0](9.0/), [10.1](10.1/), and [11.0](11.0/). For general Tomcat usage, consult the [upstream Tomcat image documentation](https://hub.docker.com/_/tomcat).

## License

Apache Tomcat is distributed under the [Apache License 2.0](https://www.apache.org/licenses/LICENSE-2.0). Base image and other bundled software may have separate licenses; users are responsible for checking the licenses applicable to their use.