# get-selected-item-in-viewmodel-from-tapcommand-in-.net-maui-listview

How to get selected item in ViewModel from TapCommand in .NET MAUI LISTVIEW?

## Sample

```xaml
<syncfusion:SfListView
        x:Name="listView"
        ItemSize="100"
        ItemsSource="{Binding BookInfo}"
        SelectedItems="{Binding SelectedItems}"
        SelectionGesture="Tap"
        SelectionMode="Multiple"
        TapCommand="{Binding TapCommand}">

    <syncfusion:SfListView.ItemTemplate>
        <DataTemplate>
            <Grid Padding="10">
                <Grid.RowDefinitions>
                    <RowDefinition Height="0.4*" />
                    <RowDefinition Height="0.6*" />
                </Grid.RowDefinitions>
                <Label
                    FontAttributes="Bold"
                    FontSize="21"
                    Text="{Binding BookName}"
                    TextColor="Teal" />
                <Label
                    Grid.Row="1"
                    FontSize="15"
                    Text="{Binding BookDescription}"
                    TextColor="Teal" />
            </Grid>
        </DataTemplate>
    </syncfusion:SfListView.ItemTemplate>
</syncfusion:SfListView>
```

```c#
public class BookInfoRepository
{
    private ObservableCollection<object>? selectedItems = new ObservableCollection<object>();

    public ObservableCollection<object>? SelectedItems
    {
        get { return selectedItems; }
        set { this.selectedItems = value; }
    }

    public ICommand TapCommand { get; set; }

    public BookInfoRepository()
    {
        GenerateBookInfo();
        TapCommand = new Command(ExecuteTapCommamd);
    }

    private void ExecuteTapCommamd(object obj)
    {
        // SelectedItems contains the currently selected items.
        var _selectedItems = this.SelectedItems;
    }
}
```

## Requirements to run the demo

* [Visual Studio 2017](https://visualstudio.microsoft.com/downloads/) or [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/)
* Xamarin add-ons for Visual Studio (available via the Visual Studio installer).

## Troubleshooting

### Path too long exception

If you are facing path too long exception when building this example project, close Visual Studio and rename the repository to short and build the project.
