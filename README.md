# SatelliteBox-Swift

A description of this package.

## Features
- Scan for devices.
- Connect to device.
- Write value to device.
- Disconnect device.

## Usage

```swift

import UIKit
import SatelliteBox_Swift

class ViewController: UIViewController {
    
    var myBluetoothList      = [M_UserBluetooth]()
    var myBluetoothSelected  : M_UserBluetooth!

    override func viewDidLoad() {
        super.viewDidLoad()
    }
    
    func setupScanning() {
        
        BT_Manager().setupScan_BT { [self] (results) in
            
            myBluetoothList.removeAll()

            if results.count != 0 {
                
                myBluetoothList  = results //Save search information to use in various functions.

            } else {

                print("Device not found.")
            }
        }
    }
    
    func setupSelectedExample() {
        
        //In this case, the first device selection event is simulated.
        myBluetoothSelected = myBluetoothList[1]
    }
    
    func setupFunctionExample() {
        
        //Originally, the data was organized in a set of instructions.
        //After selecting the device You can enter a value at "myBluetoothSelected.peripheral", "myBluetoothSelected.ipDevice" and "myBluetoothSelected.rssi" in function

        BT_Manager().setupConnect_BT(peripheral: myBluetoothSelected.userPeripheral, ipDevice: myBluetoothSelected.userIpDevice, rssi: myBluetoothSelected.userRSSI) { result in
            
            if result.userConnected == true {
                
                    print("Connection success.")

            } else {
                
                    print("Connection failed.")
            }
        }
        
        //You can deploy the selected data model at "peripheral" by myBluetoothSelected.peripheral
        //You can take the prepared data cubes. to send to the device at "link"
        
        BT_Manager().setupWriteValue_BT(peripheral: myBluetoothSelected.userPeripheral, link: "") { (status) in
            
            if status == true {

                print("succeeded in writing the value")

            } else {
                print("Failed to write value.")
            }
        }
        
        //You can deploy the selected data model at "peripheral" by myBluetoothSelected.peripheral

        BT_Manager().setupDidConnect_BT(peripheral: myBluetoothSelected.userPeripheral) { status in
            
            if status == true {
                
                print("Success to disconnect.")
                
            } else {

                print("Unable to disconnect.")
            }
        }
    }
}

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
