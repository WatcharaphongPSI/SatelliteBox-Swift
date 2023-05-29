# SatelliteBox-Swift

A description of this package.

## Features
- Scan for devices.
- Connect to device.
- Write value to device.
- Disconnect device.

## Usage

```swift

//You need to import library on your head class.
import SatelliteBox-Swift

```

```swift

// You can find all devices in this function.
BT_Manager().setupScan_BT(completion: <#T##([M_UserBluetooth]) -> Void#>)

// Usage Example

var myBluetoothList      = [M_UserBluetooth]()

func setupInitBluetooth() {

    BT_Manager().setupScan_BT { [self] (results) in
        
        if results.count != 0 {
            
            myBluetoothList    = results

        } else {

            print("Device not found.")
        }
    }
}

BT_Manager().setupConnect_BT(peripheral: <#T##Peripheral#>, ipDevice: <#T##String#>, rssi: <#T##Int#>, completion: <#T##(M_UserBluetooth) -> Void#>)

BT_Manager().setupWriteValue_BT(peripheral: <#T##Peripheral#>, link: <#T##String#>, completion: <#T##(Bool) -> Void#>)

BT_Manager().setupDidConnect_BT(peripheral: <#T##Peripheral#>, completion: <#T##(Bool) -> Void#>)
    
```

## Swift Package Manager

Simply add the package dependency to your Package.swift and depend on "SatelliteBox-Swift" in the necessary targets:
```swift
dependencies: [
    .package(url: "https://github.com/WatcharaphongPSI/SatelliteBox-Swift.git")
]
```

> Don't forget the Privacy Description in `info.plist`.
<img src="./Sources/SatelliteBox-Swift/Images/PrivacyDescription.png">

## Requirements
SatelliteBox-Swift requires iOS 13.0+
