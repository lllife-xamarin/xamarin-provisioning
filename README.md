## Error

>> "Error: No installed provisioning profiles match the installed iOS code signing keys"

#### Log ที่มีปัญหา

```
Target _DetectSdkLocations:
Task "DetectSdkLocations"
    Using task DetectSdkLocations from Xamarin.iOS.Tasks.DetectSdkLocations, Xamarin.iOS.Tasks, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null
      DeveloperRoot: /Applications/Xcode.app/Contents/Developer
      DevicePlatform: /Applications/Xcode.app/Contents/Developer/Platforms/iPhoneOS.platform
      GetPlatformPath: /Applications/Xcode.app/Contents/Developer/Platforms/iPhoneOS.platform
      Searching for 'SDK Usr directory' in '/Applications/Xcode.app/Contents/Developer/Platforms/iPhoneSimulator.platform/Developer/usr'
      Searching for 'SDK Usr directory' in '/Applications/Xcode.app/Contents/Developer/usr'
      Searching for 'SDK bin directory' in '/Applications/Xcode.app/Contents/Developer/usr/bin'
    DetectSdkLocations Task
      TargetFrameworkIdentifier: Xamarin.iOS
      TargetArchitectures: i386
      SdkVersion: 9.3
      XamarinSdkRoot: /Library/Frameworks/Xamarin.iOS.framework/Versions/Current
      SdkRoot: /Applications/Xcode.app/Contents/Developer/Platforms/iPhoneSimulator.platform/Developer/SDKs/iPhoneSimulator9.3.sdk
      SdkDevPath: /Applications/Xcode.app/Contents/Developer
      SdkUsrPath: /Applications/Xcode.app/Contents/Developer/usr
      SdkPlatform: iPhoneSimulator
      SdkIsSimulator: True
Done executing task "DetectSdkLocations"
Done building target "_DetectSdkLocations" in project "/Users/wk/Source/xamarin/hanselman.forms/Hanselman.iOS/Hanselman.iOS.csproj".
Done building target "_DetectSdkLocations" in project "/Users/wk/Source/xamarin/hanselman.forms/Hanselman.iOS/Hanselman.iOS.csproj" ("/Library/Frameworks/Mono.framework/External/xbuild/Xamarin/iOS/Xamarin.iOS.Common.targets"); "_DetectSigningIdentity" depends on it.

Target _DetectSigningIdentity:
Task "DetectSigningIdentity"
    Using task DetectSigningIdentity from Xamarin.iOS.Tasks.DetectSigningIdentity, Xamarin.iOS.Tasks, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null
    DetectSigningIdentity Task
      AppBundleName: HanselmaniOS
      AppManifest: Info.plist
      Keychain: <null>
      ProvisioningProfile: <null>
      RequireCodesigning: False
      SdkPlatform: iPhoneSimulator
      SdkIsSimulator: True
      SigningKey: iPhone Developer
/Library/Frameworks/Mono.framework/External/xbuild/Xamarin/iOS/Xamarin.iOS.Common.targets: error : No installed provisioning profiles match the installed iOS signing identities.
```

#### Log ปกติ

```
Target _DetectSdkLocations:
Task "DetectSdkLocations"
    Using task DetectSdkLocations from Xamarin.iOS.Tasks.DetectSdkLocations, Xamarin.iOS.Tasks, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null
      DeveloperRoot: /Applications/Xcode.app/Contents/Developer
      DevicePlatform: /Applications/Xcode.app/Contents/Developer/Platforms/iPhoneOS.platform
      GetPlatformPath: /Applications/Xcode.app/Contents/Developer/Platforms/iPhoneOS.platform
      Searching for 'SDK Usr directory' in '/Applications/Xcode.app/Contents/Developer/Platforms/iPhoneSimulator.platform/Developer/usr'
      Searching for 'SDK Usr directory' in '/Applications/Xcode.app/Contents/Developer/usr'
      Searching for 'SDK bin directory' in '/Applications/Xcode.app/Contents/Developer/usr/bin'
    DetectSdkLocations Task
      TargetFrameworkIdentifier: Xamarin.iOS
      TargetArchitectures: i386
      SdkVersion: 9.3
      XamarinSdkRoot: /Library/Frameworks/Xamarin.iOS.framework/Versions/Current
      SdkRoot: /Applications/Xcode.app/Contents/Developer/Platforms/iPhoneSimulator.platform/Developer/SDKs/iPhoneSimulator9.3.sdk
      SdkDevPath: /Applications/Xcode.app/Contents/Developer
      SdkUsrPath: /Applications/Xcode.app/Contents/Developer/usr
      SdkPlatform: iPhoneSimulator
      SdkIsSimulator: True
Done executing task "DetectSdkLocations"
Done building target "_DetectSdkLocations" in project "/Users/wk/Source/xamarin/xamarin-forms-fsharp/iOS/Hello.iOS.fsproj".
Done building target "_DetectSdkLocations" in project "/Users/wk/Source/xamarin/xamarin-forms-fsharp/iOS/Hello.iOS.fsproj" ("/Library/Frameworks/Mono.framework/External/xbuild/Xamarin/iOS/Xamarin.iOS.Common.targets"); "_DetectSigningIdentity" depends on it

Target _DetectSigningIdentity:
Task "DetectSigningIdentity"
    Using task DetectSigningIdentity from Xamarin.iOS.Tasks.DetectSigningIdentity, Xamarin.iOS.Tasks, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null
    DetectSigningIdentity Task
      AppBundleName: Hello.iOS
      AppManifest: Info.plist
      Keychain: <null>
      ProvisioningProfile: <null>
      RequireCodesigning: False
      SdkPlatform: iPhoneSimulator
      SdkIsSimulator: True
      SigningKey: iPhone Developer
    Detected signing identity:
      Code Signing Key: "iPhone Developer: xxx@gmail.com (xxx)" (xxxxxx)
      Bundle Id: com.bcircle.hello
      App Id: com.bcircle.hello
Done executing task "DetectSigningIdentity"
Done building target "_DetectSigningIdentity" in project "/Users/wk/Source/xamarin/xamarin-forms-fsharp/iOS/Hello.iOS.fsproj".
```

## Device provisioning

หลังจาก Activate Xamarin.iOS ถ้าต้องการเทสโปรแกรมกับ iPhone ต้อง Provision device เสียก่อน คือต้องบอก Apple ว่าเราจะติดตั้งโปรแกรมลงไปในเครื่อง

## ขั้นตอน

- สมัคร Apple id
- สมัคร Developer program
- Generate development certificate
- เพิ่ม  iOS Device
- สร้าง Provisioning profile / Team provisioning profile
- ..

## Link

- https://github.com/xamarin/xamarin-macios/blob/2edb2ae4f5bb371a7006731987717c01f8725420/msbuild/Xamarin.MacDev.Tasks.Core/Tasks/DetectSigningIdentityTaskBase.cs
- https://developer.xamarin.com/guides/ios/getting_started/installation/device_provisioning
