# SatelliteBox-Swift

A description of this package.

## Features
- Scanning for devices.
- Connected to device.
- Send value to device.
- Disconnect device.

## Usage

```swift
import SatelliteBox-Swift

// You can find all devices in this function.
BT_Manager().setupScan_BT { [self] (results) in
             
}    
```

## Swift Package Manager

Simply add the package dependency to your Package.swift and depend on "SatelliteBox-Swift" in the necessary targets:
```swift
dependencies: [
    .package(url: "https://github.com/WatcharaphongPSI/SatelliteBox-Swift.git")
]
```

## Requirements
SatelliteBox-Swift requires iOS 13.0+
