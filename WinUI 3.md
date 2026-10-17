### Navigation
- **Frame** (`Microsoft.UI.Xaml.Controls`): navigation container. Key methods: `Navigate()`, `GoBack()`, `GoForward()`. Specific to UWP/WinUI/XAML.
- **OnNavigatedTo**: Page override called when the page becomes the active page in a Frame. Use it to receive the navigation parameter and load data.
- **OnNavigatingFrom**: Page override called just before the user leaves the page. Use it to save state or cancel the navigation.

### XAML basics
- **Loaded**: event raised when the element is built and added to the visual tree. Use it for initialization that needs the UI to exist.
- **x:Name**: gives an element a name so code-behind can access it directly (e.g. `MyButton.Content = "Hi"`).
- **Page.Resources**: a resource dictionary scoped to the page, for styles, brushes, converters and templates that the page's controls reuse via `{StaticResource Key}`.

### Data and lists
- **ObservableCollection<T>**: a collection that notifies the UI when items are added or removed, so a bound list updates automatically.
- **INotifyPropertyChanged**: interface that lets a property notify the UI when its value changes. Raise `PropertyChanged` in the setter.
- **Displaying a list of items**: bind a `ListView` or `GridView` to an `ObservableCollection` through `ItemsSource`, and define how each item looks with an `ItemTemplate` (a `DataTemplate`).

```xml
<ListView ItemsSource="{x:Bind Items}">
    <ListView.ItemTemplate>
        <DataTemplate x:DataType="local:Item">
            <TextBlock Text="{x:Bind Name}"/>
        </DataTemplate>
    </ListView.ItemTemplate>
</ListView>
```

## Windows SDK

| Class | Namespace | Purpose / key methods |
|---|---|---|
| **StorageFolder** | `Windows.Storage` | Represents a folder: `CreateFileAsync`, `GetFilesAsync`, `GetFolderAsync`. From the Windows Runtime, so it also works in UWP. |
| **StorageFile** | `Windows.Storage` | Represents a file: `CopyAsync`, `DeleteAsync`, `MoveAsync`. |
| **FileIO** | `Windows.Storage` | Static helper for reading and writing a `StorageFile`: `ReadTextAsync`, `WriteTextAsync`. |
