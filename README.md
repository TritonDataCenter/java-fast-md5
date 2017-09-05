# java-fast-md5

This is a fork of [Timothy W. Macinta's FastMD5
project](http://www.twmacinta.com/myjava/fast_md5.php) by
[Joyent](https://joyent.com) for distribution through [Maven
Central](http://central.sonatype.org/).

We've left the package name unmodified in order to spare users from
having to download or build new versions of the native library.

## Usage

Add a Maven dependency:

```xml
<dependency>
    <groupId>com.joyent.util</groupId>
    <artifactId>fast-md5</artifactId>
    <version>2.7.1</version>
</dependency>
```

Please note: classes are defined under the `com.twmacinta.util` package
despite the differing group ID. This is required to maintain binary
compatibility with native library files distributed at the original project page.

### Native Lirary

Set the `com.twmacinta.util.MD5.NATIVE_LIB_FILE` system property to the
absolute path of your architecture's compiled library file (`.jnilib` or `.so`).

### Explicitly disable native library

Set the `com.twmacinta.util.MD5.NO_NATIVE_LIB` system property to `1` or `true`
to prevent loading of native library files. This takes precedence over `NATIVE_LIB_FILE`.

### Native library autodiscovery

When neither the `NATIVE_LIB_FILE` nor `NO_NATIVE_LIB` properties are set
The following paths will be checked automatically:

- `${CWD}/lib/arch/${OS}_${ARCH}/MD5.${EXT}`
- `${CWD}/lib/MD5.${EXT}`
- `${CWD}/MD5.${EXT}`

Where `${EXT}` is based on `${OS}` using the following table:

| OS      | EXT    |
|---------|--------|
| darwin  | jnilib |
| freebsd | so     |
| linux   | so     |
| windows | dll    |
| default | so     |

Original project notes follow.

This is a fast implementation of the MD5 algorithm written in Java.
For details, see the project website at:

    http://www.twmacinta.com/myjava/fast_md5.php
