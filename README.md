# Introduction

This is a maven repo of some of my projects which I don't want to put onto maven central. Currently, it includes:
- Hex Casting
- Inline
- Patchouli

I might add more here if I want to.

To browse my repo, just check this page. A file directory reading / clicking system a normal maven repository like maven central doesn't exist here. That page will just lead to a 404. 

IIRC, there is a 100GB per month of access in Github Pages. Please don't repeatedly download stuff from here. Github will also hunt you down for it (jk).

# Usage

## Including my repository

This is how you can use it.

In your gradle, add a new repository like so:
```groovy
repositories {
  // ... (all your other repositories)
  maven { url = "https://an-m1654.github.io/maven/" }
  // ... (all your other repositories)
}
```

Now, you can use my libraries like how you would with others.

## Example

An example with inline-common is as follows (inline is a Minecraft dependency so it is modImplementation):

build.gradle:
```groovy
dependencies {
  modImplementation "com.samsthenerd.inline:inline-common:$minecraftVersion-$inlineVersion"
}
```

gradle.properties:
```properties
minecraftVersion=1.21.4
inlineVersion=1.2.2
```

# Architecture of this maven repository (For those who are curious and don't know)

I followed this structure designed by Apache [here](https://maven.apache.org/repository/layout.html).

It's actually very simple to add a new library. I run gradle publish to my own local repo (NOT the one in .m2/repository.
I specify a publish repository which is a file path on my computer to a location that I placed this git repository in,
then run publishXXXXToMavenRepository, not publishXXXToMavenLocal), then do a `git add .`, then `git push`. The new
library would now be here.
