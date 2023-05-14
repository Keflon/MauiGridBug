# MAUI BUG
## ScrollView in Grid cell multiple issues on iOS, Android and WinUI.


### `Grid` with `RowDefinitions="*,*"` where each grid cell contains a `ScrollView` ...
### Scenario 1:  
```xaml
<Grid RowDefinitions="*,*">
    <ScrollView Grid.Row="0" >
        <Rectangle HeightRequest="500" BackgroundColor="Blue"/>
    </ScrollView>
    <ScrollView Grid.Row="1" >
        <Rectangle  HeightRequest="500" BackgroundColor="Yellow" />
    </ScrollView>
</Grid>
```
1. Android: The `Grid` cells are 50/50 and the `Rectangle` can be scrolled within the `ScrollView`. (Pixel 5, Emulator)  
1. iOS: **[BUG]** The `Grid` cells expand to fit the `Rectangle`, i.e. they are too big. (iPhone SE, simulator)  
1. Windows: **[BUG]** The `Grid` cells appear to be the correct height but the `Rectangles` are minimal height.   

Image 1.1  
![image](https://github.com/dotnet/maui/assets/16598898/d722db90-58e7-40d1-9362-d6f37bc9d143)

Image 1.2  
![image](https://github.com/dotnet/maui/assets/16598898/b8723edf-2f79-4619-9de5-44288f3d76f4)

Image 1.3  
![image](https://github.com/dotnet/maui/assets/16598898/81a030e0-4540-4bd8-8b26-58590e4a0eba)

### Scenario 2:
```xaml
<Grid RowDefinitions="*,*">
    <ScrollView Grid.Row="0" >
        <Button Text="A Button in a ScrollView" HeightRequest="500" BackgroundColor="Blue"/>
    </ScrollView>
    <ScrollView Grid.Row="1" >
        <Button Text="A Button in a ScrollView" HeightRequest="500" TextColor="Blue" BackgroundColor="Yellow" />
    </ScrollView>
</Grid>
```
1. Android: The Grid cells are 50/50 and the Buttons can be scrolled within the ScrollView.   
    1. Android: **[BUG]** If this text has InputTransparent=True, it does not show.  
1. iOS: **[BUG]** The Grid cells expand to fit the Button, i.e.they are too big. (iPhone SE, simulator)  
1. Windows: **[BUG]** The Grid is 50/50, the Button is 500 in height, but the ScrollView is not scrollable.  

Image 2.1  
![image](https://github.com/dotnet/maui/assets/16598898/14f136e9-f4b2-4210-88cd-db9e597c9d53)

Image 2.2  
![image](https://github.com/dotnet/maui/assets/16598898/0e09df63-0afb-41e3-a6be-1926ca37db18)

Image 2.3  
![image](https://github.com/dotnet/maui/assets/16598898/4cbc4208-ad74-4284-bdc8-2ed4db44341c)

