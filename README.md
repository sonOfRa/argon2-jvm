# Argon2 Binding for the JVM

This is a JVM binding for [Argon2](https://github.com/P-H-C/phc-winner-argon2).

## Maven
Add [this Bintray Maven repository](https://bintray.com/phxql/maven/argon2-jvm/view#) to your settings.
You can then use the following Maven coordinates:
```
<dependency>
    <groupId>de.mkammerer</groupId>
    <artifactId>argon2-jvm</artifactId>
    <version>1.0</version>
<dependency>
```
## Gradle
```
repositories {
    maven {
        url  "https://dl.bintray.com/phxql/maven"
    }
}

dependencies {
    compile 'de.mkammerer:argon2-jvm:1.0'
}
```
## Usage
This binding needs the Argon2 C library. Libraries for the following operation systems are included:
* Linux x86
* Linux x86-64

If your operating system isn't in the list, you have to specify the `jna.library.path`. See [this documentation](https://java-native-access.github.io/jna/4.2.1/com/sun/jna/NativeLibrary.html) for details.

```
// Create instance
Argon2 argon2 = Argon2Factory.create();

// Hash password
String hash = argon2.hash(2, 65536, 1, "password");

// Verify password
if (argon2.verify(hash, "password")) {
    // Hash matches password
} else {
    // Hash doesn't match password
}
```

## Technical details
This library uses [JNA](https://github.com/java-native-access/jna) to communicate with the Argon2 C library.

## Building it yourself
Run `./gradlew clean build` to build and test the software.

## License
[LGPL v3](https://www.gnu.org/licenses/lgpl.html)

## Maintainer
Moritz Kammerer ([@phXql](https://github.com/phxql))