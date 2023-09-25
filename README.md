# flutter_google_places_sdk

Original package: 
[![pub package](https://img.shields.io/pub/v/flutter_google_places_sdk.svg)](https://pub.dartlang.org/packages/flutter_google_places_sdk)

![Tests](https://github.com/matanshukry/flutter_google_places_sdk/actions/workflows/tests.yml/badge.svg)

A Flutter plugin for google places sdk that uses the native libraries on each platform.
Check out [Rational](##RATIONAL) below to understand why you should use this plugin.

## Usage

To use this plugin, add to yaml: 

flutter_google_places_sdk:
    git:
      url: https://github.com/FelipeRinconVillegas1/FLUTTER-GOOGLE-PLACES-SDK.git
      ref: main

## Rational

By now you probably found some other plugins, and wondering why this one was even created.
Well, there's a good reason for that.

All other plugins will use http web requests rather than the native sdk.

Google allows you to limit the usage of your api key to your android application.
However, that only works when you're using the native SDK.

So when using the http web requests method, you can't actually limit it,
and if someone can get your API key (usually not a problem if it's in a mobile client),
it can be used anywhere outside of it.

## Example

``` dart
import 'package:flutter/material.dart';
import 'package:flutter_google_places_sdk/flutter_google_places_sdk.dart';

void main() {
  runApp(MaterialApp(
    home: Scaffold(
      body: Center(
        child: ElevatedButton(
          onPressed: () async {
            final places = FlutterGooglePlacesSdk('my-key');
            final predictions =
                await places.findAutocompletePredictions('Tel Aviv');
            print('Result: $predictions');
          },
          child: Text('Predict and print to console'),
        ),
      ),
    ),
  ));
}


