# **WPF (TODO: CRIAR REPOSITÓRIO EM INGLES E COLOCAR ISSO)**

* WPF and WinForms are not the same
  * WinForms came first and is the easiest to use
  * WinForms is kinda old
  * WinForms is not good for generating graphics (images, videos, etc), because they get the memory from the cpu
  * WPF gets the memory from Gpu to put graphics
* DataBidings is really important
* WPF uses XAML (ZAMAL)
  * Its almost a HTML
* DONT DRAG AND DROP IN WPF, try to avoid it
  * Mostly vecause of the locations that apper automatically in the XAML.
* The grid tag is where pretty much all elements will be inside.
  * We should put more grids inside to separate the things.
* Use the tag Grid.ColumnDefinitions to say hou many columns will exist in the window.
   * Inside this, we put a ColumnDefinition, setting the width
   * Its a self closing tag
   * We have to put one for every column we want
      * A tip: Put the first and last one with a small width, so it creates like a border, to prevent that elements go way too much to the edge. 
   * AVOID AS MUCH POSSIBILE STE HEIGHTS AND WIDTHS WITH NUMBERS, instead use "auto".
     * Nut in the edges like a I said before, its ok to use the number, because is something that we ALWAYS want ot be like that, whatever the screen size is.
   * If we put a "*" as a width/height value, it means it will get the rest of the screen, the part there's not definition to it **(TODO: STUDY MORE ABOUT STARS)**
     * It will grow or shrink depengin on how fill up are the other auto columns
     * If you have two stars columns, each column will take half of the leftovers.
 * Do the same for the rows with the tags Grid.RowDefinitions and RowDefinition.
   * Maybe even put more rows, because probrably will have more information.
 * Use the tag TextBlock for labels
   * To say where the label will be, we have to write the column and row that we want to put the info.
     * `<TextBlock Grid.Column="1" Grid.Row = "1">` Putting like this will make the label go to the SECOND (because it starts at 0) column and row that we defined (and in this case, they are set to auto)
   * We close the tag, and we put the text inside the tags.
   * Inside the tag, we can put properties like FontSize, FontFamily, Text, etc.
     * Using the text, means we don't need to write in beetwen the tags and can use the text block as a self closing tag.
 * WPF got style hierarchy like CSS.
   * Because of that we have a global syle, that we can set to the whole application (we can see this at the properties panel of the tag)
     * Inside the window tag, we can set the global properties.
   * So because of that, if we dont specify something, it will get from the global style.
 * The window height and width, is the starting size, not the full size.
 * To create a text box to wrtie on, we use the TextBox tag
   * If we want to give a name to the refrence of our TextBox, we put a property like `x:Name = "Nome"`
     * The name is optional in all tags, we just use it if we want to access it later via code in C#.
   * Self closing tag
   * Dont forget to add the postion with the column and row.
   * We can put a size to make the text box bigger.
 * We can use the property Grid.ColumnSpan to sya that the content of the tag can use more space, and in this property we say how many columns will it use in total.
   * We can use this when theres like a title that is way to big and is making the other things look far, because its making this auto column way too big.
 * Use the margin property to make the contents of each tag dont be so close.
 * Button have a tag with this same name.
   * THe content property is what will be the text insisde.
 * Now to atuamatically create a method to what happens when the user click on the button (The Event handlers):
   * Go to the properties panel, on the side of that name thre is like a lightining, clicking on that and it will open all the methods you can create, including the click
   * The method we created will use the name we defined as the name of the element together with the action slected.
   * It will create om the xaml.cs
 * To use the value of the tags in the code, we can call the name of the tag and see the properties.
 * In a ComboBox tag, we can assign the values in the constructor, we have to assign those values to the ItemSource property
   * An then inside the tag we have to define the property of the class that we will use as values.
 * Use the tag Image to put an image.
   * We have to put a source to the image, and it will adjust together with the size of the window.
 * MediaElement is the tag to video, and it also needs a source.
 * StackPanel is like a grid, where we can stack elements.
   * We have the property to choose the orientation.
   * WrapPanel is like the same, but will show the elements depending of the free space.
   * We can put this inside a ComboBox to puth an image together with the values.
 * ScrollViewer to put elements with scroll.
 * The properties of the placment need to be only on the parent element, and not on the child elements.

SPEAK ABOUT DATA BINDINGS
EVENT HANDLERS

### MVVM
* Lauch the viewmodel, and not a mainwindow directly,
* Models is the data
* Views which are for the UI
* ViewModels are the drivers, the code that supports the view are here.
* 