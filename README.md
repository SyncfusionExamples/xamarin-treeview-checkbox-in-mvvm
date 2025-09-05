# How to use checkbox in MVVM in .NetMaui-treeview ?

## About the samples

This example describes how SfTreeView works with checkbox. 

## Sample

### XAML
```xaml
<ContentPage.BindingContext>
    <local:FileManagerViewModel x:Name="viewModel"/>
</ContentPage.BindingContext>

<TreeView:SfTreeView x:Name="treeView"
                     ItemsSource="{Binding Folders}"
                     ItemTemplateContextType="Node"
                     CheckBoxMode="Recursive"
                     AutoExpandMode="RootNodesExpanded"
                     CheckedItems="{Binding CheckedItems}">
    
    <TreeView:SfTreeView.HierarchyPropertyDescriptors>
        <TreeViewEngine:HierarchyPropertyDescriptor TargetType="{x:Type local:Folder}" ChildPropertyName="Files"/>
        <TreeViewEngine:HierarchyPropertyDescriptor TargetType="{x:Type local:File}" ChildPropertyName="SubFiles"/>
    </TreeView:SfTreeView.HierarchyPropertyDescriptors>
    
    <TreeView:SfTreeView.ItemTemplate>
        <DataTemplate>
            <ViewCell>
                <ViewCell.View>
                    <Grid Padding="5">
                        <SfButtons:SfCheckBox 
                        x:Name="CheckBox"
                        Text="{Binding Content.FileName}"
                        IsChecked="{Binding IsChecked, Mode=TwoWay}"/>
                    </Grid>
                </ViewCell.View>
            </ViewCell>
        </DataTemplate>
    </TreeView:SfTreeView.ItemTemplate>
</TreeView:SfTreeView>
```

### View Model
```csharp
private ObservableCollection<object> checkedItems;

public ObservableCollection<object> CheckedItems
{
    get { return checkedItems; }
    set { this.checkedItems = value; }
}

checkedItems = new ObservableCollection<object>();
checkedItems.Add(doc);
checkedItems.Add(typeScript);
checkedItems.Add(uiGuide);
checkedItems.Add(stone);
checkedItems.Add(wind);
checkedItems.Add(song);
```

## Requirements to run the demo
Visual Studio 2017 or Visual Studio for Mac.
Xamarin add-ons for Visual Studio (available via the Visual Studio installer).

## Troubleshooting
### Path too long exception
If you are facing path too long exception when building this example project, close Visual Studio and rename the repository to short and build the project.

## License

Syncfusion® has no liability for any damage or consequence that may arise from using or viewing the samples. The samples are for demonstrative purposes. If you choose to use or access the samples, you agree to not hold Syncfusion® liable, in any form, for any damage related to use, for accessing, or viewing the samples. By accessing, viewing, or seeing the samples, you acknowledge and agree Syncfusion®'s samples will not allow you seek injunctive relief in any form for any claim related to the sample. If you do not agree to this, do not view, access, utilize, or otherwise do anything with Syncfusion®'s samples.

