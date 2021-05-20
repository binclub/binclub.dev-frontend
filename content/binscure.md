+++
title = "Binscure Java Obfuscator"
description = "Binscure protects your Java applications from reverse engineering and piracy"
template = "page.html"

[extra]
keys = "binscure obfuscate obfuscator java jvm kotlin security protection drm decompilation bytecode"
+++

# Binscure

Binscure is an obfuscator for any application that runs on the JVM - this includes Java, Kotlin, and Scala applications.

Obfuscating your application:
* Protects against intellectual property theft
* Protects your application from being pirated or "cracked"
* Discourages and hinders the discovery of security vulnerabilities in your application

## Compatibility

|Version | Status|
|---|---|
|Java 6 and under|Not Supported|
|Java 7|Working but not tested|
|Java 8-15|Supported and regularly tested|
|Java 16|Supported|

## How it works

Binscure is a simple terminal application that is ran as `java -jar binscure.jar [configuration_file]`.
The configuration file is a yaml formatted file - an example can be found [here](https://github.com/binclub/BinscureDocumentation/blob/master/exampleConfig.yml).

Binscure will accept an input file as any ZIP style archive containing `.class` files.
This includes formats such as JAR but does **not** include formats like APK.
If your application is running on a regular JDK it is very likely that your application will be compatible.
If your application is not formatted in this way you should [contact us](/contact) to discuss the possibility of adding support.

Binscure will then go through each `.class` file and apply modifications to the class to hinder the ability for reverse engineers and reverse engineering tools to analyse the classes.
These modifications should not result in any noticeable change in the behaviour of the application, however they might increase the file size and decrease the performance of your classes depending on how Binscure is configured.

The modified `.class` files will then be rewritten to the specified output file, along with any other resources found within the input.

Many tools will become unusable (nearly every decompiler) and the ones that are usable will normally provide confusing or hard to understand output.

## Operations

Below are some of the operations Binscure performs:

* **Constant Obfuscation** - constants such as strings and numbers will be obfuscated so that they do not appear in the application's files but are instead dynamically calculated at runtime. This prevents information leaks such as API keys, passwords or URLs.
* **Call Obfuscation** - method calls which are normally easy to read and follow are instead calculated dynamically at runtime. This makes the flow of your application harder to follow and prevents people searching your applications for uses of interesting methods, such as those related to networking or cryptography.
* **Flow Obfuscation** - typical control flow such as loops, switches and if statements are obscured as generic switch statements over obscure inputs calculated using hard to understand mathematical equations.
* **Mathematical Obfuscation** - operations such as addition, subtraction and more are replaced with alternative operations which can not be easily understood or evaluated, see [our blog post on this](https://blog.binclub.dev/006-Mixed-Boolean-Arithmetic/) for more detailed information.
* **Stripping Debug Information** - Sensitive information intended for debugging purposes can be removed including line numbers, variable names and original file names.

## Performance

Applying Binscure to your application will always have a negative performance impact - this is inevitable.
Luckily Binscure offers "severity" configuration.
This allows you to configure a trade-off between high security and negligible performance degredation.

## Evaluation

If you would like to evaluate the obfuscator before purchasing you can [contact us](/contact) to ask us to obfuscate either our own demo application or your own small demo application.
We will then send you back the obfuscated output and you can evaluate the strength of the protection yourself.

## Purchasing

**[Click here for purchasing instructions](/purchasing)**.

|Plan Name                  |Description                                                 |Offline Usage     |Perpetual Updates |Support           |Commercial Usage  |Source Access|Price (GBP) |
|---------------------------|------------------------------------------------------------|------------------|------------------|------------------|------------------|------------------|------|
|Multinational Company      |Companies declaring taxable revenue in more than one country|<green>Yes</green>|<green>Yes</green>|<green>Yes</green>|<green>Yes</green>|<green>Yes</green>|£5,000|
|Partnership or company     |Non-individual legal entities                               |<green>Yes</green>|<green>Yes</green>|<green>Yes</green>|<green>Yes</green>|<red>No</red>     |£1,000|
|Individual (Commercial)    |Individuals                                                 |<green>Yes</green>|<green>Yes</green>|<green>Yes</green>|<green>Yes</green>|<red>No</red>     |£250  |
|Individual (Non-Commercial)|Individuals for non-commercial purposes                     |<green>Yes</green>|<green>Yes</green>|<green>Yes</green>|<red>No</red>     |<red>No</red>     |£100  |

Commercial licenses allow you to use the obfuscator in commercial environments - i.e. obfuscating proprietary software which you charge for.
Non-commercial licenses are for hobbyists who want to prevent their intellectual property while still distributing their applications for free.

If you have any questions about the plans you can always [contact us](/contact).

Licenses are **usable only by the entity that purchases them** (or on behalf of that entity, e.g. an employee or building your software on a CI/CD server).
Giving your license to, or using your license on behalf of another entity is in breach of your license.

While these prices may seem high, we believe they are fair:
* Many of our competitors charge you to recieve updates. All updates to Binscure are free.
* Licenses entitle you to use the software on as many computers as you like, by as many employees as you like.
* The repetitive costs saved from piracy or dealing with intellectual property theft are often far less than these (one time) prices.

If you have unique circumstances that you feel should be factored into your price, or are simply unable to afford our prices, please [contact us](/contact).
We are more than happy to arrange personalised quotes.

## Changelog

You can view Binscure's changelog (March 2020-Present) [here](/binscure/changelog).
