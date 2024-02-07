# svg-icon

This "may or may not" work for your use case, but it's something that I definitely wish I had known about sooner. Sites like [Fontello](https://fontello.com/) allow you to import your .svg icons and consolidate them into a font.ttf file containing your custom icon (or any of the standard icons they provide). When I imported my **parent-pin-collapsed.svg** file and exported to **my-svg-icons** here is the result.

[![demo][1]][1]

Here's a brief overview of the process:

[![where it goes][2]][2]

___
**Xaml**

```xaml
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


  [1]: https://i.stack.imgur.com/JVXv9.png
  [2]: https://i.stack.imgur.com/kVWRv.png