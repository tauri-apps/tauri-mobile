# bevy-demo

This is a modified version of [Niklas Eiker's Bevy Game Template](https://github.com/NiklasEi/bevy_game_template) with a `#[mobile_entry_point]` attribute on `main`, which generates all the boilerplate `extern` functions for mobile.

To run this on desktop, just do `cargo run` like normal! For mobile, use `cargo android run` and `cargo apple run` respectively (or use `cargo android open` and `cargo apple open` to open in Android Studio and Xcode respectively).
