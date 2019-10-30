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