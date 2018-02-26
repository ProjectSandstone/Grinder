# PURPOSE

This is a purpose, maybe it will be developed someday, or maybe not.

# Grinder
Grinds Sandstone into your plugin jar

# What is grinder

Grinder is the Sandstone tool that grinds the [SandstoneAPI](https://github.com/ProjectSandstone/SandstoneAPI) and adds it into your plugin jar, removing the requirement to have Sandstone plugin installed on platform, and even if installed, the Sandstone of your plugin jar will be used instead of the installed one.

## Small

Grinder breaks Sandstone into small pieces, removing things that you haven't used in the plugin (like functions, services, classes).

## Easy

Grinder is easy to use, it can be used as command line tool or integrated with Gradle through `grinder integrate gradle`.

## Fast (purpose, see [#1](https://github.com/ProjectSandstone/Grinder/issues/1))

# Details

Grinder only works with [SandstoneAPI](https://github.com/ProjectSandstone/SandstoneAPI) and does not support [SandstoneCommon](https://github.com/ProjectSandstone/SandstoneCommon) features (like adapter), the base implementation of the API used to be added to your jar is [SandstoneRuntime](https://github.com/ProjectSandstone/SandstoneRuntime).

# Under the hood

Grinder analyzes Sandstone and determines which things that should be removed before adding the Sandstone to the jar, then it updates [SandstoneRuntime](https://github.com/ProjectSandstone/SandstoneRuntime) with plugin definitions (such as id, name, version, dependencies).

# How to use
 
## Base plugin
 
Grinder will download a simple gradle project and configure the integration.
 
Command:
```sh
grinder create :base-plugin
```
 
## Build
 
If the project is a gradle project and integration is configured, grinder will call `gradle build`, otherwise, grinder will try to find the jar of the project in `build/libs/` and will add grinded Sandstone to it.

Command:
```sh
grinder build
```
 
#### Grind
 
Grind is the task invoked by `build` before it adds the Sandstone the your project, this will get Sandstone dependency jar and grind it, the saved jar can be found in the working directory of grinder.

#### Platform-specific

Grinder will add [SandstoneRuntime](https://github.com/ProjectSandstone/SandstoneRuntime) with all platform implementations, if you want to build platform-specific jars you should configure grinder in gradle or use the command below.

```sh
grinder build --platform-split
```

This will tell grinder to generate a plugin jar for each platform.

```sh
grinder build --platform sponge
```

This will tell grinder to generate a plugin jar for sponge only.

```sh
grinder build --platform sponge bukkit
```

This will tell grinder to generate a plugin jar for sponge and bukkit.
