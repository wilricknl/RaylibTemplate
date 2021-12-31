# Raylib Template

Get up and running quickly with Raylib on Windows using Visual Studio. Follow the installation and add my template to your Visual Studio installation. You then are able to quickly create a new project where Raylib is already statically linked.

- [Raylib Template](#raylib-template)
- [1. Requirements](#1-requirements)
- [2. Installation](#2-installation)
  - [2.1 Cloning Raylib](#21-cloning-raylib)
  - [2.2 Building](#22-building)
  - [2.3 Setup environment](#23-setup-environment)
  - [2.4 Add template](#24-add-template)
- [3. FAQ](#3-faq)

# 1. Requirements

* [Visual Studio Community 2022](https://visualstudio.microsoft.com/vs/) with the workload _Desktop development with C++_
* [Git](https://git-scm.com/)

# 2. Installation

## 2.1 Cloning Raylib

Open a new **developer** command prompt and enter the following commands to clone Raylib:

```
cd C:\
mkdir SDKs
git clone https://github.com/raysan5/raylib.git
cd raylib
```

Keep this command prompt open for the building stage.

## 2.2 Building

Next build the static configurations of Raylib as follows:

```
cd projects\VS2019
devenv raylib.sln /build "Release" /project raylib
devenv raylib.sln /build "Debug" /project raylib
devenv raylib.sln /build "Release|x86" /project raylib
devenv raylib.sln /build "Debug|x86" /project raylib
```

## 2.3 Setup environment

The template will use the environment variable `RAYLIB` as a pointer to the root folder of Raylib. Create a new user or system variable to point to the root folder of Raylib:
* Variable name: `RAYLIB`
* Variable value: `C:\SDKs\raylib`

## 2.4 Add template

From the releases page of this repository download `Raylib Static.zip` and put it in `%UserProfile%\Documents\Visual Studio 2022\Templates\ProjectTemplates`. Next time you open Visual Studio the new template shoud be added.

# 3. FAQ

> How to remove the console window from my Raylib project?

Go to project settings and set the following properties for **all configurations** and **all platforms**:

1. In _Linker > System_ set _SubSystem_ to `Windows`
2. In _Linker > Commandline_ add `/ENTRY:"mainCRTStartup"`
