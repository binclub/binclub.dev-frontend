+++
title = "Binscure Changelog"
description = "Changelog for the Binscure Obfuscator"
template = "page.html"

[extra]
keys = "binscure obfuscate obfuscator java jvm kotlin security protection drm decompilation bytecode"
+++

# Binscure Changelog

#### 0.8 (2021-04-12)

* Remove lazyLibraryLoading
* Add support for multiple in/out sources:

```yaml
sources:
  - input: in.jar
    output: out.jar
  - input: second.jar
    output: second-obf.jar
```

* Support for field and local variable obfuscation. Fields will be replaced with invokedynamic operations, Local variables will be obfuscated using raw unsafe memory access

```yaml
indirection:
  # indy method call transformations
  methodCalls: true
  # indy field access transformations
  fieldAccesses: true
  # raw memory variable access transformations
  variableAccesses: true
  # minimum local variables in method to apply raw memory transforms
  # too low will result in worthless memory allocations for tiny methods
  variableAccessesMinVariables: 5
```

* Added `stringObfuscation.maxLength` option to prevent creating obfuscated strings so large they can't be written
* Added `flowObfuscation.mergeVersion` option to force set the version of merged classfiles produced by `flowObfuscation.mergeMethods`
* Add ability to exclude items from obfuscation based on their annotation, e.g. `@full/path/to/Annotation`

#### 0.7 (2021-02-15)

* Java 17 support
* Added crasher for the Recaf reverse engineering tool, enabled with `crasher.recaf`

#### 0.6 (2020-11-30)

* Add method parameter obfuscation. An integer parameter will be added to methods. This parameter will be a "secret" and will be constantly modified throughout the callstack. The integer will be used as keys in flow obfuscation and string decryption. To retrieve the value of the secret, an attacker would have to simulate the entire callstack

```yaml
methodParameter:
  enabled: true
```

* Fix an issue where String Obfuscation combined with Flow Obfuscation's class merger would result in strings being improperly decrypted
* Runtime and obfuscation time performance improvements

#### 0.5 (2020-11-03)

* Fix remapper with indys
* Better outputs on failures such as when a class fails to write
* Huge optimisations
* Exclusions ending with `;` will only match exactly (i.e. not if it is a prefix). Exclusions ending with `-` will only match if it starts with and does not equal the exclusion
* Remove BadClinitExploit as it has been patched in OpenJDK 15
* Fix indirection obfuscation in OpenJDK 15
* Add new option `flowObfuscation.noverify` which inserts unverifiable bytecode. To work obfuscated jars will need to be run with `-noverify` option, or use `flowObfuscation.java8` option which will produce classes which only work on OpenJDK <= 8 or OpenJ9 but use an exploit to bypass the verification process.
* Add mixed boolean arithmetic obfuscation:
```yaml
arithmetic:
  enabled: true
  # Number of times to recursively apply the substitutions
  repeat: 3
```
* Fix source stripper ignoring exclusions
* Add ability to exclude callsites in indirection obfuscation
* Fix ClassCastException when using indirection

#### 0.4 (2020-07-03)

* Added an configuration option lazyLibraryLoading which is enabled by default. This option will only load classes from specified libraries when necessary, helping both performance and memory usage (~200x faster obfuscation in some cases)

#### 0.3 (2020-07-01)

* An edge case which resulted in string obfuscation causing a verifier error has now been fixed
* You can now specify exclusions per transformer, i.e. only exclude a package from being renamed while still having flow obfuscation
* Various other minor bug fixes

#### 0.2 (2020-06-09)

* Better progress printing during class and resource saving
* Added `shuffleClasses`, `shuffleMethods`, `shuffleFields`, `resetLineProgress` and `printProgress` configuration options to the root configuration
* Optimise manifest remapping speed greatly
* Make JSON and Manifest remapping more consistent
* Fix an error occuring when invokedynamic instructions were relocated to a new method by the static method merger
* Rename some binscure generated fields that some JVMs refused to verify
* Fix BadClinitExploit not checking if classes were excluded
* Fix enum values optimiser not checking if it was enabled

#### 0.1 (2020-03-06)

* Public beta release
