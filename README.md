# How to use checkbox in treeview?
This example illustrates how to use checkbox in treeview.

#   Getting Started with Xamarin CheckBox (SfCheckBox)

##  Adding SfCheckBox reference
You can add SfCheckBox reference using one of the following methods:

##  Method 1: Adding SfCheckBox reference from nuget.org

Syncfusion Xamarin components are available in nuget.org. To add SfCheckBox to your project, open the NuGet package manager in Visual Studio, search for Syncfusion.Xamarin.Buttons, and then install it.

##  Method 2: Adding SfCheckBox reference from toolbox

Syncfusion also provides Xamarin Toolbox. Using this toolbox, you can drag the SfCheckBox control to the XAML page. It will automatically install the required NuGet packages and add the namespace to the page. To install Syncfusion Xamarin Toolbox, refer to Toolbox.

##  Method 3: Adding SfCheckBox assemblies manually from the installed location

If you prefer to manually reference the assemblies instead referencing from NuGet, add the following assemblies in respective projects.

#   Create a Simple SfCheckBox
The Xamarin CheckBox (SfCheckBox) control is configured entirely in C# code or by using XAML markup. The following steps explain how to create a SfCheckBox and configure its elements.

##  Add namespace for referred assemblies

**[XAML]**
```
xmlns:syncfusion="clr-namespace:Syncfusion.XForms.Buttons;assembly=Syncfusion.Buttons.XForms"
```
Refer SfCheckBox control with declared suffix name for Namespace

**[XAML]**

```
<ContentPage>
    <ContentPage.Content>
        <StackLayout>
              <syncfusion:SfCheckBox x:Name="checkBox"/>
        </StackLayout>
    </ContentPage.Content>
</ContentPage>
```
#   Checkbox in treeview
**[XAML]**
```      
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
```
##  ViewModel

**[C#]**

```
 public class FileManagerViewModel
    {
        private ObservableCollection<object> checkedItems;

        public ObservableCollection<object> CheckedItems
        {
            get { return checkedItems; }
            set { this.checkedItems = value; }
        }

        public ObservableCollection<Folder> Folders { get; set; }
        
        public FileManagerViewModel()
        {
            this.Folders = GetFiles();
        }

        private ObservableCollection<Folder> GetFiles()
        {
            var nodeImageInfo = new ObservableCollection<Folder>();
            Assembly assembly = typeof(MainPage).GetTypeInfo().Assembly;

            var doc = new Folder() { FileName = "Documents"};
            var download = new Folder() { FileName = "Downloads"};
            var mp3 = new Folder() { FileName = "Music"};
            var pictures = new Folder() { FileName = "Pictures"};
            var video = new Folder() { FileName = "Videos"};

            var pollution = new File() { FileName = "Environmental Pollution.docx"};
            var globalWarming = new File() { FileName = "Global Warming.ppt"};            

            var games = new File() { FileName = "Game.exe"};
            var tutorials = new File() { FileName = "Tutorials.zip"};
            var typeScript = new File() { FileName = "TypeScript.7z"};
            var uiGuide = new File() { FileName = "UI-Guide.pdf"};

            var song = new File() { FileName = "Gouttes"};

            var camera = new File() { FileName = "Camera Roll"};
            var stone = new File() { FileName = "Stone.jpg"};
            var wind = new File() { FileName = "Wind.jpg"};

            var img0 = new SubFile() { FileName = "WIN_20160726_094117.JPG"};
            var img1 = new SubFile() { FileName = "WIN_20160726_094118.JPG"};

            var video1 = new File() { FileName = "Naturals.mp4"};
            var video2 = new File() { FileName = "Wild.mpeg"};

            doc.Files = new ObservableCollection<File>
            {
                pollution,
                globalWarming
            };

            download.Files = new ObservableCollection<File>
            {
                games,
                tutorials,
                typeScript,
                uiGuide
            };

            mp3.Files = new ObservableCollection<File>
            {
                song
            };

            pictures.Files = new ObservableCollection<File>
            {
                camera,
                stone,
                wind
            };
            camera.SubFiles = new ObservableCollection<SubFile>
            {
                img0,
                img1
            };

            video.Files = new ObservableCollection<File>
            {
                video1,
                video2
            };

            nodeImageInfo.Add(doc);
            nodeImageInfo.Add(download);
            nodeImageInfo.Add(mp3);
            nodeImageInfo.Add(pictures);
            nodeImageInfo.Add(video);

            checkedItems = new ObservableCollection<object>();
            checkedItems.Add(doc);
            checkedItems.Add(typeScript);
            checkedItems.Add(uiGuide);
            checkedItems.Add(stone);
            checkedItems.Add(wind);
            checkedItems.Add(song);

            return nodeImageInfo;
        }
    }
```
