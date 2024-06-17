## What's Canvas SDK

Canvas SDK is a JavaScript library that contains everything developers need to create new widgets.

Widgets are Miro entities, similar to stickies and images. They can be interactive, animated, and use high-fidelity graphics.

New widgets can be developed without modifying the Miro codebase. This allows to rapidly expand Miro capabilities and eventually, also open up Widget development to third parties.

## Before you begin

1. Make sure you've [set up VPN](https://miro.atlassian.net/wiki/spaces/IT/pages/1954349066/Cloud+VPN+Prisma+Access+-+Connection+Steps).
2. Clone the Canvas SDK repository to your machine. This monorepo contains various project published as NPM packages.

    ```bash
    git clone git@github.com:miroapp-dev/surface.git
    ```

## Setting up the environment

Make sure you have installed:

1. [Brew](#brew)
2. [Xcode](#xcode)
3. [Python 3](#python)
4. [NPM](#npm)
5. [Bazel](#bazel)

### Brew

Install [Brew](https://brew.sh/).

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

### Xcode

Install [Xcode](https://apps.apple.com/fr/app/xcode/id497799835?mt=12) version 12 or higher.

To check the version of Xcode, run:

```bash
/usr/bin/xcodebuild -version
```

The result should look similar to this:

```bash
Xcode 15.0.1
Build version 15A507
```

Check that `xcode-select` is configured to use `xcodebuild`, not command line tools:

```bash
xcode-select -p
/Applications/Xcode.app/Contents/Developer
``` 

If you get some other response, run:

```bash
sudo xcode-select --switch /Applications/Xcode.app/Contents/Developer
```

Additionally, make sure to clean Bazel cache by running `bazel clean --expunge`.

### NPM

Your NPM credentials must be set up correctly. Run the following command to check your credentials:

```bash
npm whoami
```

The result should print you username.

**⚠️ Important**: If you get a different response or an error, follow these steps to [configure private registry credentials](https://github.com/miroapp-dev/client/blob/master/documentation-portal/docs/setup.md#configure-private-registry-credentials).

### Python

You should have Python 3 installed and `python3` command should work:

```bash
python3 --version
Python3 3.11.5
```

If you get a different response, you may need to symlink `python` to `python3`, or run `brew install python3` to install Python 3.

### Bazel

Everything is built using [Bazel](https://bazel.build/). We use Bazelisk — a wrapper for Bazel, which automatically picks the right version of Bazel with respect to your current working directory and downloads it from the official server.

To install Bazelisk, use one of the following methods:

1. With [brew](https://docs.bazel.build/versions/0.29.1/install-os-x.html#step-2-install-the-bazel-homebrew-package): `brew install bazelisk`
2. With [npm](https://www.npmjs.com/package/@bazel/bazelisk): `npm install -g @bazel/bazelisk`

## Explore Canvas SDK

The Canvas SDK contains the following projects:

1. [WidgetClient](#widgetclient-playground)
2. [CanvasAPI](#canvasapi)
3. [SurfaceWidgetSDK](#surfacewidgetsdk)
4. [New Engine](#new-engine)
5. [WidgetEditor](#widgeteditor)

### WidgetClient playground

A standalone playground to explore the rendering engine and SurfaceWidgetSDK.

Inside of the `/surface` folder, run the following command to start the playground:
_This command can take a while when you run it for the first time_

```bash
bazel run //:WidgetClient
```

Open the browser and navigate to [http://localhost:8080/](http://localhost:8080/).

- **Language**: TypeScript
- **Location**: `src/Frontend/WidgetClient/`
- [README](https://github.com/miroapp-dev/surface/blob/master/src/Frontend/WidgetClient/README.md)

### CanvasAPI

TBD: A declarative, stateless, and retained mode graphics API.

- **Language**: TypeScript
- **Location**: `src/CanvasAPI/`
- **API documentation**: _TBA_
- [README](https://github.com/miroapp-dev/surface/blob/master/src/CanvasAPI/README.md)

### SurfaceWidgetSDK

TBD: An SDK for developing widgets using a React-like API.

- **Language**: TypeScript
- **Location**: `src/SurfaceWidgetSDK/`
- [API documentation](https://invisionapp.atlassian.net/wiki/spaces/EXTINTEGRATIONS/pages/2627731581/WidgetSDK+Documentation)
- [README](https://github.com/miroapp-dev/surface/blob/master/src/SurfaceWidgetSDK/README.md)

### New Engine

2D-vector rendering engine for SurfaceWidgetSDK.

- **Language**: C++
- **Location**: all `.cpp` files in `src/`
- [API documentation](https://test-reports.studio/engine-public-api-docs/)
- [README](https://github.com/miroapp-dev/surface/blob/master/README.engine.md)

### WidgetEditor

A React component that wraps the Monaco Code Editor fully configured for developing widgets.

- **Language**: TypeScript
- **Location**: `src/WidgetEditor/`
- [README](https://github.com/miroapp-dev/surface/blob/master/src/WidgetEditor/README.md)

## Read more

1. [Confluence: Canvas SDK overview](https://miro.atlassian.net/wiki/spaces/PT/pages/3316876020/Widget+SDK+documentation)
2. [Confluence: Synced state](https://miro.atlassian.net/wiki/spaces/PT/pages/3317170498/Widget+SDK+Synced+State)
3. [Miro: Technical overview](https://miro.com/app/board/uXjVNERW_9w=/)
