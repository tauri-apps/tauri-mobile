# cargo-mobile2

> _The answer to "how do I use Rust on iOS and Android?"_
>
> cargo-mobile takes care of generating Xcode and Android Studio project files, building and running on device, generating project boilerplate, and a few other things!

This project is a fork of [cargo-mobile](https://github.com/BrainiumLLC/cargo-mobile/). Tauri uses it as a library dependency instead of using its CLI directly. For more information, please visit Tauri's [prerequisites](https://v2.tauri.app/start/prerequisites/#configure-for-mobile-targets) and [development](https://v2.tauri.app/develop/#developing-your-mobile-application) guides..

In the meantime, cargo-mobile2 contains the template of wry, please follow [wry's instruction](https://github.com/tauri-apps/wry#android--ios) if you want to use with it.

## Installation

The build will probably take a bit, so feel free to go get a snack or something.

```bash
cargo install --git https://github.com/tauri-apps/cargo-mobile2
```

cargo-mobile2 is currently supported on macOS, Linux and Windows. Note that it's not possible to target iOS on platforms other than macOS! You'll still get to target Android either way.

You'll need to have Xcode and the Android SDK/NDK installed. Some of this will ideally be automated in the future, or at least we'll provide a helpful guide and diagnostics.

Whenever you want to update:

```bash
cargo mobile update
```

## Usage

To start a new project, all you need to do is make a directory with a cute name, `cd` into it, and then run this command:

```bash
cargo mobile init
```

After some straightforward prompts, you'll be asked to select a template pack. Template packs are used to generate project boilerplate, i.e. using the `wry` template pack gives you a [wry](https://github.com/tauri-apps/wry) project that runs out-of-the-box on desktop and mobile.

| name | info                                                                                                                |
| ---- | ------------------------------------------------------------------------------------------------------------------- |
| wry  | Minimal wry project                                                                                                 |
| egui | Full egui + winit + wgpu example based on [agdk-egui example](https://github.com/rust-mobile/rust-android-examples) |

**Template pack contribution is welcomed**

> **Note**
>
> For all the templates available now, currently `bevy` templates do not work and will encounter compile error if you try to build the project.

Once you've generated your project, you can run `cargo run` as usual to run your app on desktop. However, now you can also do `cargo apple run` and `cargo android run` to run on connected iOS and Android devices respectively!

If you prefer to work in the usual IDEs, you can use `cargo apple open` and `cargo android open` to open your project in Xcode and Android Studio respectively.

For more commands, run `cargo mobile`, `cargo apple`, or `cargo android` to see help information.

### Android

`cargo android run` will build, install and run the app and follows device logs emitted by the app.

By default, warn and error logs are displayed. Additional logging of increasing verbosity can be shown by use of the `-v` or `-vv` options. These also provide more verbose logging for the build and install steps.

For fine-grained control of logging, use the `--filter` (or `-f`) option, which takes an Android log level, such as `debug`. This option overrides
the default device logging level set by `-v` or `-vv`.

If using the `android_logger` crate to handle Rust log messages, `trace` logs from Rust are mapped to `verbose` logs in Android.
