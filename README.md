# Maui icon from SVG file

This "may or may not" work for your use case, but it's something that I definitely wish I had known about sooner. Sites like [Fontello](https://fontello.com/) allow you to import your **.svg** icons and consolidate them into a font.ttf file containing glyphs for your custom icons (and/or any of the standard icons they provide). When I imported my **parent-pin-collapsed.svg** file and exported to **my-svg-icons** here is the result.

[![demo][1]][1]

Here's a brief overview of the process:

[![where it goes][2]][2]

___
**Xaml**

```xaml
<!--So easy to make an icon-->
<Button
    x:Name="CounterBtn"
    Text="&#xE801;"
    FontFamily="my-svg-icons"
    Clicked="OnCounterClicked"
    HorizontalOptions="Center">
    <Button.Background>
        <LinearGradientBrush StartPoint="0,0" EndPoint="1,1">
            <GradientStop Color="LightBlue" Offset="0" />
            <GradientStop Color="DarkBlue" Offset="1" />
        </LinearGradientBrush>
    </Button.Background>
</Button>
```

___
**Importing the font**

*This honestly seems to be optional on platforms other than WinUI...*

Per [Stephen Quan's answer](https://stackoverflow.com/a/77278771/5438626) make sure you register your font in MauiProgram.cs, i.e.

```csharp
public static class MauiProgram
{
    public static MauiApp CreateMauiApp()
    {
        var builder = MauiApp.CreateBuilder();
        builder
            .UseMauiApp<App>()
            .ConfigureFonts(fonts =>
            {
                fonts.AddFont("OpenSans-Regular.ttf", "OpenSansRegular");
                fonts.AddFont("OpenSans-Semibold.ttf", "OpenSansSemibold");
                fonts.AddFont("my-svg-icons.ttf", "my-svg-icons");
            });

#if DEBUG
    	builder.Logging.AddDebug();
#endif

        return builder.Build();
    }
}
```


  [1]: https://i.stack.imgur.com/JVXv9.png
  [2]: https://i.stack.imgur.com/kVWRv.png