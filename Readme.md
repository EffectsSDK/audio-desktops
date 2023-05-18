# Audio Enhancement SDK - Windows trial SDK and Demo samples

Add real-time AI audio enhancement that makes audio meeting experience more effective and comfortable to your application in a few hours. Remove background audio noise and keep clear speech that is much less annoying to listen to and cause less listener fatigue.

This repository contains the trial version of the C++ Audio SDK that you can integrate into your project/product to see how it will work in real conditions.

Also, there is the Demo Application with Audio SDK integration, so you can just run it right away and see SDK in action.


## Technical Details

- SDK is available for Windows 10+ x64/x86 platforms
- macOS support is upcoming

## Features

- Real time speech denoising and audio enhancement

## Demo Application

Run the demo app right now on your machine. Download the demo app from the [releases](https://github.com/EffectsSDK/audio-desktops/releases) page. Test it on predefined audio records, WAV files, or your mic.

A Sample SDK integration application is also provided, see `examples` folder in the SDK.

The result of processing noisy WAV file by the SDK:

![TS Audio SDK Demo results](audio_results.PNG?raw=true "Demo results")

## Obtaining an Audio SDK License

To receive an Audio SDK license, please fill in the contact form on the [effectssdk.com](https://effectssdk.com/contacts) website.

## Usage  details

SDK is provided as a set of dynamic libraries (DLLs on Windows).

To create an asynchronous audio filter:

``` cpp
auto factory = createTSAudioFactory();

auto filter = factory->createNoiseSuppressionFilter(
    &callback,
    ts_audio::NoiseSuppressionPreset::Quality);
```

Push an audio buffer to the filter:

``` cpp
auto buffer = factory->createAudioBuffer(
    samplesData,
    samples * sizeof(float), // byte count
    sampleRate,
    numChannels,
    ts_audio::SampleType::Float32,
    timestamp
);

filter->process(buffer);
```

See `examples` folder for a complete sample.
