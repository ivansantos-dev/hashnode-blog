## SwiftUI not keeping state in ObservableObject

So as I am struggling through learning SwiftUI, I ended facing an issue where my data was not being refreshed when redrawing the entire UI. The issue was simple but I am slow. So here is what the issue was.

I have the following view:
```
struct ContentView: View {
    @EnvironmentObject var loginViewModel: LoginViewModel

    var body: some View {
        NavigationView {
            if loginViewModel.signedIn {
                GroceryListsView()
            } else {
                LoginView()
            }
        }
        .navigationViewStyle(StackNavigationViewStyle())
        .onAppear {
            loginViewModel.signedIn = loginViewModel.isSignedIn
        }
    }
}
```
This is pretty standard the LoginView has a @State signedIn that gets update once you login.

And my App is as follows:
```
struct GroceryListApp: App {
    let persistenceController = PersistenceController.shared
    @StateObject var groceryViewModel = GroceryViewModel(context: PersistenceController.shared.container.viewContext)
    
    @UIApplicationDelegateAdaptor(AppDelegate.self) var appDelegate
    
    var body: some Scene {
        WindowGroup {
            let loginViewModel = LoginViewModel()
            ContentView()
                .environment(\.managedObjectContext, persistenceController.container.viewContext)
                .environmentObject(loginViewModel)
                .environmentObject(groceryViewModel)
        }
    }
}
``` 

I was able to login, and then able to view my grocery items in next view. However, every time I updated the grocery list, the app would go back to the login page. So it meant that the every time the List() in GroceryView() gets updated, the UI gets redrawned, and then it would load the LoginView(). 

Can you spot the problem? Duhh pretty obvious. Not to me as a beginner following Youtube videos! But anywho, here is the fix:

```
struct GroceryListApp: App {
    let persistenceController = PersistenceController.shared
    
    @StateObject var groceryViewModel = GroceryViewModel(context: PersistenceController.shared.container.viewContext)
    @StateObject var loginViewModel = LoginViewModel()
    
    @UIApplicationDelegateAdaptor(AppDelegate.self) var appDelegate
    
    var body: some Scene {
        WindowGroup {
            ContentView()
                .environment(\.managedObjectContext, persistenceController.container.viewContext)
                .environmentObject(loginViewModel)
                .environmentObject(groceryViewModel)
            
        }
    }
}
```

You just have to move the loginViewModel to a @StateObject and then every works smoothly.

Hopefully this helps you if you face the same issue.

Best of luck!


System.exit(0)


