jackson-dataformat-soap
========

[![Apache License 2](https://img.shields.io/badge/license-ASF2-blue.svg)](https://choosealicense.com/licenses/apache-2.0/)
[![](https://img.shields.io/maven-central/v/ru.sokomishalov.jackson/jackson-dataformat-soap)](https://mvnrepository.com/artifact/ru.sokomishalov.jackson/jackson-dataformat-soap)
[![](https://img.shields.io/jitpack/v/github/sokomishalov/jackson-dataformat-soap)](https://jitpack.io/#sokomishalov/jackson-dataformat-soap)

## Overview

Jackson SOAP implementation over jackson-dataformat-xml

## Distribution

Maven:

```xml

<dependency>
    <groupId>ru.sokomishalov.jackson</groupId>
    <artifactId>jackson-dataformat-soap</artifactId>
    <version>x.y.z</version>
</dependency>
```

Gradle kotlin dsl:

```kotlin
implementation("ru.sokomishalov.jackson:jackson-dataformat-soap:x.y.z")
```

## Usage

Used [this SOAP message](./src/test/resources/example/get_person_output_ws_addr.xml) for deserialization in example below.
```kotlin
fun main() {
    val mapper = SoapMapper()
    val content = this.javaClass.getResource("/example/get_person_output_ws_addr.xml").readText()
    val deserialized: SoapEnvelope<SoapAddressingHeaders, GetPersonOutput> = mapper.readValue(content)
    val serialized = mapper.writeValueAsString(deserialized)
}
```