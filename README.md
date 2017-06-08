# Globeport.Client.Uwp.Host

This is a test project demonstrating the use of the Globeport Elements UWP native host. Globeport is a new platform built on a zero knowledge framework, enabling rapid development of cross platform, interactive content, powered by XAML and Javascript. 

[Globeport Elements](https://www.microsoft.com/en-gb/store/p/globeport-elements/9nblggh4whtb) is an integrated development environment available on the Windows Store (currently in preview).It enables realtime development of interactive components with live preview and instant submissions. It is designed to be familiar to Windows developers although a minimal working knowledge of javascript is required. Once submitted, elements can be hosted within the [Globeport social network](https://www.microsoft.com/en-gb/store/p/globeport/9nblggh6jzc3), within your own native UWP applications and in the browser. Native hosts for other platforms are in the pipeline!

# Nuget Installation

1. Install the Nuget package

```
Install-Package Globeport.Client.Uwp.Host
```

2. Add the following extensions to the `Package.appxmanifest` file in your project (hoping to automate this step in a future release.

```
<Extensions>
    <Extension Category="windows.activatableClass.inProcessServer">
        <InProcessServer>
            <Path>libsodium-uwp.dll</Path>
            <ActivatableClass ActivatableClassId="Sodium.Core" ThreadingModel="both" />
            <ActivatableClass ActivatableClassId="Sodium.CryptoHash" ThreadingModel="both" />
            <ActivatableClass ActivatableClassId="Sodium.GenericHash" ThreadingModel="both" />
            <ActivatableClass ActivatableClassId="Sodium.GenericHashAlgorithmProvider" ThreadingModel="both" />
            <ActivatableClass ActivatableClassId="Sodium.GenericHashAlgorithmNames" ThreadingModel="both" />
            <ActivatableClass ActivatableClassId="Sodium.KDF" ThreadingModel="both" />
            <ActivatableClass ActivatableClassId="Sodium.KeyPair" ThreadingModel="both" />
            <ActivatableClass ActivatableClassId="Sodium.OneTimeAuth" ThreadingModel="both" />
            <ActivatableClass ActivatableClassId="Sodium.PasswordHash" ThreadingModel="both" />
            <ActivatableClass ActivatableClassId="Sodium.PublicKeyAuth" ThreadingModel="both" />
            <ActivatableClass ActivatableClassId="Sodium.PublicKeyBox" ThreadingModel="both" />
            <ActivatableClass ActivatableClassId="Sodium.ScalarMult" ThreadingModel="both" />
            <ActivatableClass ActivatableClassId="Sodium.SealedPublicKeyBox" ThreadingModel="both" />
            <ActivatableClass ActivatableClassId="Sodium.SecretBox" ThreadingModel="both" />
            <ActivatableClass ActivatableClassId="Sodium.SecretKeyAuth" ThreadingModel="both" />
            <ActivatableClass ActivatableClassId="Sodium.SecretAead" ThreadingModel="both" />
            <ActivatableClass ActivatableClassId="Sodium.ShortHash" ThreadingModel="both" />
            <ActivatableClass ActivatableClassId="Sodium.StreamEncryption" ThreadingModel="both" />
            <ActivatableClass ActivatableClassId="Sodium.Utilities" ThreadingModel="both" />
        </InProcessServer>
    </Extension>
</Extensions>
```
