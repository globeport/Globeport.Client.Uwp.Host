# Globeport.Client.Uwp.Host

This project demonstrates the use of the Globeport Elements UWP native host. Globeport is a new platform built on a zero knowledge framework, enabling rapid development of cross platform, interactive content, powered by XAML and Javascript. 

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
        <Path>Lumia.Imaging.dll</Path>
        <ActivatableClass ActivatableClassId="Lumia.Imaging.BufferProviderImageSource" ThreadingModel="both" />
      </InProcessServer>
    </Extension>
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


# Usage

Add a reference to the following namespace in your XAML control or page

```
xmlns:globeport="using:Globeport.Client.Uwp.Host"
```

## 1. Elements

Add a Globeport Element and set its Id property e.g.

```
<Grid>
    <globeport:Element Id="3MNPB7380400"/>
</Grid>
```

The element Id can be accessed by clicking `Web Link` on the menu within Globeport. This will open the element in the browser and the Id can then be extracted from the Url e.g.

https://api.globeport.io/v1.0/entities/3MNPB7380400/render

So the Id for this element is **3MNPB7380400**

## 2. Controls

Add a Globeport Control and set its Id property e.g.

```
<Button>
    <Button.Flyout>
        <Flyout>
            //a color picker
            <globeport:Control x:Name="ColorPicker" Id="3OST61540400" EventRaised="ColorPicker_EventRaised"/>
        <Flyout>
    </Button.Flyout>
</Button>
```

The control Id can currently be accessed by clicking the 'Edit' button on the resource toolbar within Globeport Elements. This will display the resource Url e.g.

https://api.globeport.io/v1.0/resources/3OST61540400/render

So the Id for this control is **3OST61540400**


# API

Both controls expose the following API. You will have to refer to the respective control/element within Globeport Elements for details of its internal implementation.

### Properties

`string Id { get; set; }` 
- Sets the unique instance Id for the control/element. Refer to above for details on how to find this.

### Methods

`object GetProperty(string name)` 
- Gets a property value by name. e.g. GetProperty("Color")

`void SetProperty(string name, object value)`
- Sets a property value by name. e.g. SetProperty("Color", "#000000")

### Events

`event EventHandler<DataObject> EventRaised`
- a custom event that can be invoked by a control or element e.g. ColorChanged. The DataObject type encapsulates a JSON object


# Feedback

Please let me know your thoughts on this and if you'd like to help build the platform please let me know. Thanks, Stuart.

stuart@globeport.io

www.globeport.io

# Screenshots

A collage of native Globeport elements embedded in a UWP app.

![Globeport Host Screenshot](https://github.com/globeport/Globeport.Client.Uwp.Host/blob/master/screenshot.png "Globeport Elements")
