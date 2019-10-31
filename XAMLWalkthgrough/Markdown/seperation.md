# Creation of a basic XAML UI

Below shows a basic `ContentPage` coded in pure C#

```
namespace Sample
{
    public class MyPage : ContentPage
    {

        Button loginButton;
        StackLayout layout;

        public MyPage()
        {
            this.Padding = new Thickness(50)
            
            //Sets up the layout of elements on the app page.
            layout = new StackLayout
            {
                Children =
                {
                    new Label { Text = "Please log in" },
                    new Label { Text = "Username", TextColor = Color.Black },
                    new Entry (),
                    new Label { Text = "Password", TextColor = Color.Black },
                    new Entry { IsPassword = true },

                }
            };

            //Sets up a "Login" button that changes to "Clicked" when clicked
            loginButton = new Button { Text = "Login" };

            layout.Children.Add(loginButton);

            Content = layout;

            loginButton.Clicked += (sender, e) =>
            {
                Debug.WriteLine("Clicked !");
            };
        }
    }
}
```
Within this code there are 3 labels, 2 entries, and a button. Along with logic for handling when the button is clicked and some styling. This is clean and easy to read for now. As the app grows more and more elements will be added which will only add to the complexity of the code. For the benifit of the app to grow it is advisable to seperate the UI and the behavior from the start.

```
<?xml version="1.0" encoding="UTF-8"?>
<ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             x:Class="Sample.MyPage">
    <ContentPage.Content>
        <StackLayout Padding="50">
            <Label Text="Please log in" />
            <Label Text="Username" TextColor="Black" />
            <Entry />
            <Label Text="Password" TextColor="Black" />
            <Entry IsPassword="true" />
            <Button Text="Log in" Clicked="LoginButton_Clicked" />
        </StackLayout>
    </ContentPage.Content>
</ContentPage>
```

```
public partial class MyPage : ContentPage
{
    public MyPage()
    {
        InitializeComponent();
    }

    void LoginButton_Clicked(object sender, EventArgs e)
    {
        Debug.WriteLine("Clicked !");
    }
}
```
The above code set ups the same `ContentPage` but separates the UI and the behavior into a XML and C# pages repectivly. It is easy to see why this is preferable. With this set up it is possible to change the UI without needing to touch the behavior. Scaling of the application is now much easier to maintan. 