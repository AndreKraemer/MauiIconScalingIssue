# MauiIconScalingIssue
This is a repo for an issue with the scaling of .NET MAUI app icons


## Description

According to the docs at https://learn.microsoft.com/en-us/dotnet/maui/user-interface/images/app-icons?view=net-maui-7.0&tabs=android you can use the ForegroundScale Attribute of the MauiIcon element so scale your foreground layer like this:
`  <MauiIcon Include="Resources\AppIcon\appicon.svg" ForegroundFile="Resources\AppIcon\appiconfg.svg" ForegroundScale="0.65" Color="#512BD4" />`

This works fine if the decimal separator is a dot on your operating system's regional settings. If your operating system's regional settings use a comma as a decimal separator (like in most european countries), the image will, however not be scaled down if you use `ForegroundScale="0.65"`, but instead, it will be scaled up.

Because of this, the foreground of the generated icon will never fit into the background. 

## Steps to Reproduce

1. Create a File > New MAUI App on  system that uses a comma as a decimal seperator
2. Open the .csproj file and add `ForegroundScale="0.65"` to the MauiIcon element
3. Run the app on android
4. You can't see the ".NET" text in the icon any more