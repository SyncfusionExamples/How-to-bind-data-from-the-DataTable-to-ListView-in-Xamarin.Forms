# How to bind data from the datatable to listview in Xamarin.Forms
This example demonstrates how to bind the data from the datatable to listview by converting the data table rows in to the collection.

## Sample

```xaml
<Grid Margin="0">
    <sync:SfListView x:Name="listView" 
                        ItemsSource="{Binding ContactsInfo}"
                        ItemSize="70">
        <sync:SfListView.ItemTemplate>
            <DataTemplate>
                <ViewCell>
                    <ViewCell.View>
                        <Grid x:Name="grid" RowSpacing="0">
                            <Grid.RowDefinitions>
                                <RowDefinition Height="*" />
                                <RowDefinition Height="1" />
                            </Grid.RowDefinitions>
                            . . .
                            . . .
                                <Label LineBreakMode="NoWrap"
                                        TextColor="#474747" VerticalOptions="CenterAndExpand"
                                        Text="{Binding ItemArray[0]}">
                                </Label>
                                <Grid Grid.Column="1"
                                        RowSpacing="1"
                                        VerticalOptions="Center">
                                    <Grid.RowDefinitions>
                                        <RowDefinition Height="*" />
                                        <RowDefinition Height="*" />
                                    </Grid.RowDefinitions>

                                    <Label LineBreakMode="NoWrap"
                                            TextColor="#474747"
                                            Text="{Binding ItemArray[1]}">
                                    </Label>
                                . . .
                                . . .
                        </Grid>
                    </ViewCell.View>
                </ViewCell>
            </DataTemplate>
        </sync:SfListView.ItemTemplate>
    </sync:SfListView>
</Grid>

ViewModel.cs:
public ObservableCollection<object> ContactsInfo
{
   get { return contactsInfo; }
   set { this.contactsInfo = value; }
}
public void GenerateSource(int count)
{
   contactsInfo = new ObservableCollection<object>();
   dt = new DataTable("Student");
   dt.Columns.Add("ContactID", typeof(Int32));
   dt.Columns.Add("ContactName", typeof(string));
   dt.Columns.Add("ContactType", typeof(string));
   dt.Columns.Add("ContactNumber", typeof(string));

   //Data  
   for (int i = 0; i < count; i++)
   {
       dt.Rows.Add(i, CustomerNames[i], contactType[random.Next(0, 5)], random.Next(100, 400).ToString() + "-" + random.Next(500, 800).ToString() + "-" + random.Next(1000, 2000).ToString());
   }

   for (int i = 0; i < dt.Rows.Count; i++)
   {
       contactsInfo.Add(dt.Rows[i]);
   }
}
```

See [How to bind data from the datatable to listview in Xamarin.Forms](https://www.syncfusion.com/kb/9697/how-to-bind-data-from-the-dattable-to-listview-in-xamarin-forms) for more details.

## <a name="requirements-to-run-the-demo"></a>Requirements to run the demo ##

* [Visual Studio 2017](https://visualstudio.microsoft.com/downloads/) or [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/).
* Xamarin add-ons for Visual Studio (available via the Visual Studio installer).

## <a name="troubleshooting"></a>Troubleshooting ##
### Path too long exception
If you are facing path too long exception when building this example project, close Visual Studio and rename the repository to short and build the project.
