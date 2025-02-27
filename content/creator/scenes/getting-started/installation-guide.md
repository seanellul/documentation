---
date: 2018-01-01
title: Installation guide
description: Step-by-step guide to installing the SDK
aliases:
  - /documentation/installation-guide/
  - /getting-started/installation-guide/
  - /development-guide/installation-guide/
categories:
  - development-guide
type: Document
url: /creator/development-guide/installation-guide
weight: 2
---


To build scenes for Decentraland you an either use 

- The Command Line Interface (CLI)
- The visual Editor

Both tools allow you to compile and preview your scene in an "off-chain" development environment. After testing your scene locally, you can upload your content to the content server, linking it with your LAND.

**Please note:** Currently, the Decentraland SDK only supports TypeScript.

## The Decentraland Editor

The Decentraland Editor is a Visual Studio extension, that allows you to build, preview and deploy Decentraland scenes.

See installation instructions for the editor [here]({{< ref "/content/creator/editor/installation-guide.md" >}})

> Note: The Decentraland Editor is currently in alpha.


## The CLI

The Decentraland CLI is distributed via [npm](https://www.npmjs.com/get-npm?utm_source=house&utm_medium=homepage&utm_campaign=free%20orgs&utm_term=Install%20npm).

> Note: The Editor uses the CLI behind the scenes. Although the Editor is easier to use, there are some scenarios where you might need to use the CLI directly, like when building automatic publishing flows.

### Before you Begin

Please install the following dependencies before you install the CLI:

- [Node.js](https://nodejs.org) (version 8 or later)

### Install the CLI

Open the _Terminal_ app and run the following command:

```bash
npm install -g decentraland
```

Once the installation is complete, the `dcl` command will be globally available.

### Update the CLI on any platform

To update the CLI to the latest supported version, we recommend first uninstalling the CLI and then reinstalling a fresh version. To do this, run the following commands:

```bash
// uninstall
npm rm decentraland -g

// install
npm install -g decentraland
```

### Update the SDK version of a scene

If your CLI is up to date, the new projects you create with it will use the latest version of the SDK.

The SDK version used by your existing projects doesn't change by updating the CLI. You need to manually update the SDK version in the projects.

Run the following command on the scene folder:

```bash
npm i decentraland-ecs@latest
```

You can confirm that it worked by checking the `package.json` file for the scene, and looking for the `decentraland-ecs` version there.

## Troubleshooting

If you run into issues, see the [troubleshooting]({{< ref "/content/creator/scenes/debugging/troubleshooting.md" >}}) section.



<!--


#### Optional: Install Git

Mac OS and linux-based machines should have git installed by default, these steps should only be relevant to Windows based machines.

1.  Download [git](https://git-scm.com/download/win) (you'll likely want the 64-bit Windows version)
2.  The installation process will prompt you to choose severla options, we recommend the following:
	1.  Install **git bash**
	2.  For default text editor, select **Use the Nano editor by default**
	3.  For path environment, select **Use Git from the Windows Command Prompt**
	4.  For SSH executable, select **Use OpenSSH**
	5.  For HTTPS transport backend, select **Use the OpenSSL library**
	6.  For line ending conversions, select **Checkout Windows-style, commit Unix-style line endings**
	7.  For the terminal emulator to use with Git Bash select **Use MinTTY**
	8.  On the final installation screen select the following options
		- **Enable file system caching**
		- **Enable Git Credential Manager**
		- **Enable symbolic links**

-->
