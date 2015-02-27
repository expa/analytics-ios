analytics-ios
=================

analytics-ios is an iOS client for [Segment.io](https://segment.io)

Special thanks to [Tony Xiao](https://github.com/tonyxiao), [Lee Hasiuk](https://github.com/lhasiuk) and [Cristian Bica](https://github.com/cristianbica) for their contributions to the library!

## Documentation

Quickstart tutorial is available at [https://segment.io/docs/tutorials/quickstart-ios/](https://segment.io/docs/tutorials/quickstart-ios/).
Reference documentation is available at [https://segment.io/libraries/ios](https://segment.io/libraries/ios).

## Install with ExpaProvider

ExpaProvider is an add-on to send your analytics data to Expa in addition to segment.io providers.
```
git submodule update --init --remote
```
## Creating libAnalytics.a

1. Build the project (CMD+B) for iOS Device
2. Locate the libAnalytics.a file under the Products folder in the project. (Right click, show in Finder)
3. Copy Debug-iphoneos/libAnalytics.a to ~/Desktop and rename it to libAnalytics-device.a
4. Repeat & build for a 64-bit iPhone simulator
5. Copy Debug-iphonesimulator/libAnalytics.a to ~/Desktop and rename it to libAnalytics-simulator.a
6. Run the following:
```
lipo -create libAnalytics-simulator.a libAnalytics-device.a -output libAnalytics.a
```
## Adding libAnalytics to your project

You'll need to add libAnalytics.a and its headers to your project.  You can find the headers in the same folder as libAnalytics.a from the instruction #2 above (Debug-iphoneos/AnalyticsHeaders).  You'll also need to add all library dependencies to your project.  This includes:

- Optimizely.framework & Taplytics.framework
- In Build Settings, add "-lz -licucore -lsqlite3 -framework CoreBluetooth" to Other Linker Flags

The binary includes SDKs from several popular analytics libraries.  To avoid duplicate symbol errors, you may need to remove them (e.g. Mixpanel) from your Podfile, then run "pod install".

## Syntax
```
SEGAnalyticsConfiguration *configuration = [SEGAnalyticsConfiguration configurationWithWriteKey:@"YOUR-SEGMENT-WRITE_KEY"];
configuration.shouldUseLocationServices = YES;
[SEGAnalytics setupWithConfiguration:configuration];

[[SEGAnalytics sharedAnalytics] track:@"tap" properties:@{ @"button" : @"settings" }];
```

## License

```
WWWWWW||WWWWWW
 W W W||W W W
      ||
    ( OO )__________
     /  |           \
    /o o|    MIT     \
    \___/||_||__||_|| *
         || ||  || ||
        _||_|| _||_||
       (__|__|(__|__|
```

(The MIT License)

Copyright (c) 2013 Segment.io Inc. <friends@segment.io>

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the 'Software'), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED 'AS IS', WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.


[![Bitdeli Badge](https://d2weczhvl823v0.cloudfront.net/segmentio/analytics-ios/trend.png)](https://bitdeli.com/free "Bitdeli Badge")
