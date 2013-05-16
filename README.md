# sublimeText Plugin for Gradle
The sublimeText plugin allows gradle to create a Sublime Text 2 project file.

##Usage
Put the following into your build script and tweak the settings to your liking:

```groovy

apply plugin: 'sublimeText'

buildscript {
  repositories {
    maven {
      url 'http://dl.bintray.com/phildopus/maven'
    }
    dependencies {
      classpath 'us.phildop:gradle-sublimetext-plugin:0.5.1'
    }
  }
}

sublimeText {
  // enter relevant (and optional) config stuff here, explained below
}
```


####sublimeProjectName

If set, the generated file will be named &lt;sublimeProjectName&gt;.sublime-project.
Otherwise, it will default to the gradle project's name.

```groovy
sublimeText {
  sublimeProjectName = 'custom-project-name'
}
```


####defaultFileExcludePatterns &amp; defaultFolderExcludePatterns

Exclude unimportant files and folders generated by gradle and eclipse.
These will be copied to each folder entry.

```groovy
sublimeText {
  defaultFileExcludePatterns = ['.project', '.classpath', '.pydevproject']
  defaultFolderExcludePatterns = ['.gradle', 'bin', 'build', '.settings']
}
```


####addDependencyProjects

If set to true, any dependency project folders will be added.

```groovy
sublimeText {
  addDependencyProjects = true
}
```


####SublimeJava

Generate paths for [SublimeJava](https://github.com/quarnster/SublimeJava)

```groovy
sublimeText {
  generateSublimeJavaClasspath = true
  generateSublimeJavaSrcpath = true
}
```


####addGradleCompile

If set to true, generate a Sublime Text build system that calls gradle compileJava on project.

```groovy
sublimeText {
  addGradleCompile = true
}
```


####addSublimeLinterConfig

If set to true, generate configuration for [SublimeLinter](https://github.com/SublimeLinter/SublimeLinter).

```groovy
sublimeText {
  addSublimeLinterConfig = true
}
```


####EclipseJavaFormatter

Options for [EclipseJavaFormatter](https://github.com/phildopus/EclipseJavaFormatter).

```groovy
sublimeText {
  eclipseJavaFormatterConfigFile = "/path/to/config/org.eclipse.jdt.core.prefs"
  eclipseJavaFormatterSortImportsOrder = ["java", "javax", "org", "com"]
  eclipseJavaFormatterRestoreLineEndings = true
}
```


On the command line issue the following command:

```bash
gradle sublimeText
```


This plugin is licensed under the 2-clause BSD license:

```
Copyright (c) 2012-2013, Philip Oliver-Paull (phildopus)
All rights reserved.

Redistribution and use in source and binary forms, with or without
modification, are permitted provided that the following conditions are met:

1. Redistributions of source code must retain the above copyright notice, this
   list of conditions and the following disclaimer.
2. Redistributions in binary form must reproduce the above copyright notice,
   this list of conditions and the following disclaimer in the documentation
   and/or other materials provided with the distribution.

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND
ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED
WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE
DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT OWNER OR CONTRIBUTORS BE LIABLE FOR
ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES
(INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES;
LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND
ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT
(INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS
SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

```
