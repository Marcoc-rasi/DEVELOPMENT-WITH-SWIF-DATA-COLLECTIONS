# DEVELOPMENT-WITH-SWIF-DATA-COLLECTIONS

# Introduction

# Introduction

I expanded my knowledge and skills in iOS application development, building on what I learned in the `Fundamentals` course. At this stage, I focused on creating more complex and advanced applications. I worked with data coming from a server and explored new `iOS` APIs that allow for much richer application experiences. I learned how to handle `large data sets` in multiple formats, which has significantly expanded my capabilities in developing applications for the `iOS` platform.

## Videos Apps

### 1 - Tables and Persistance

#### App Anatomy and Life Cycle

##### AppEventCount-Marcocrasi

https://github.com/Marcoc-rasi/DEVELOPMENT-WITH-SWIF-DATA-COLLECTIONS/assets/51039101/76eece6c-6cbe-45d0-b426-8777ea045ae7

The code you've provided is divided into three key parts: the view controller `ViewController`, the `SceneDelegate` class, and the `AppDelegate` class. These parts work together to track and manage events related to the lifecycle of an iOS application. They are used to keep track of events and event counters, enabling the display of relevant information in the user interface.

**`ViewController.swift` - View Controller:**

In `ViewController.swift`, the `ViewController` class is defined, which inherits from `UIViewController` and is responsible for controlling the application's view. This class contains labels (`UILabels`) used to display information about events and event counters related to the application and the scene. These labels include:

- `didFinishLaunchingLabel`: A label that displays the number of times the application has been launched.
- `configurationForConectingLabel`: A label that displays how many times configurations have been made for connecting.

Additionally, variables are defined to track event counters, such as the number of times the scene has connected (`willConectToCount`), the number of times it has become active (`didBecomeActiveCount`), the number of times it has gone inactive (`willresignActiveCount`), the number of times it has entered the foreground (`willEnterForeGroundCount`), and the number of times it has gone to the background (`didEnterBackGroundCount`).

The view controller also contains a reference to `AppDelegate`, which is used to access the counters and data related to the application's lifecycle.

The `updateView` function is responsible for updating the labels in the user interface with the latest information. The labels are filled with details about events and counters, including how many times the application has been launched and how many configurations have been made to connect. The information is obtained from the `AppDelegate` instance and the count variables defined in this class.

**`SceneDelegate.swift` - SceneDelegate Class:**

The `SceneDelegate` class is used to manage events and the lifecycle of the application's scenes. It contains a series of functions that are triggered at different points in a scene's lifecycle, including:

- `scene(_:willConnectTo:options:)`: Triggered when the scene is about to connect. In this function, the `willConectToCount` counter in the view controller is incremented, and a reference to the view controller is obtained. This is done to keep track of how many times the scene has connected.

- Other functions, such as `sceneDidDisconnect`, `sceneDidBecomeActive`, `sceneWillResignActive`, `sceneWillEnterForeground`, and `sceneDidEnterBackground`, are triggered at different moments in the scene's lifecycle. These functions update the counters in the view controller and perform actions related to scene events.

**`AppDelegate.swift` - AppDelegate Class:**

The `AppDelegate` class is responsible for managing events related to the application's lifecycle. It contains properties such as `launchCount` and `configurationForConnectingCount`, which are used to track how many times the application has been launched and how many configurations have been made to connect scenes.

The most relevant functions in this class are:

- `application(_:didFinishLaunchingWithOptions:)`: Triggered when the application has finished launching. In this function, the `launchCount` counter is incremented, allowing the application's launch count to be tracked.

- `application(_:configurationForConnecting:options:)`: Triggered when a new scene session is being configured. Here, the `configurationForConnectingCount` counter is incremented each time a new scene session is configured.

- `application(_:didDiscardSceneSessions:)`: Triggered when the user discards a scene session. This function is used to release resources related to discarded scene sessions that are no longer needed.

In summary, this code is used to track and display information about events and event counters related to the application and scenes in the user interface. The `SceneDelegate` and `AppDelegate` classes are used to manage lifecycle events and counters, while the `ViewController` view controller is responsible for displaying this information in the user interface. This can be useful for debugging, usage tracking, and data collection related to the application's interaction with the user.

##### AppLifeCycle-Marcocrasi

https://github.com/Marcoc-rasi/DEVELOPMENT-WITH-SWIF-DATA-COLLECTIONS/assets/51039101/3c6a937c-8daf-4e3c-a10d-45924191abc8

The provided code relates to the management of the lifecycle of an iOS application. It consists of two main parts: the `SceneDelegate` and the `AppDelegate`. Both are crucial for controlling events and specific actions during the application's lifecycle.

The `SceneDelegate` is responsible for handling scenes in the application, including events like connecting a scene, disconnection, state changes between active and inactive, and transitions between foreground and background. Here are the key functions of the `SceneDelegate`:

- In `func scene(_ scene: UIScene, willConnectTo session: UISceneSession, options connectionOptions: UIScene.ConnectionOptions)`, I have the opportunity to configure the scene and attach the `window` to the provided scene. In this case, my code simply prints a "Scene will connect to" message and checks if the scene is an instance of `UIWindowScene`.

- In `func sceneDidDisconnect(_ scene: UIScene)`, I perform the cleanup of resources associated with the scene when it disconnects, such as when my application goes to the background or its session is discarded.

- `func sceneDidBecomeActive(_ scene: UIScene)` is called when the scene transitions from inactive to active, allowing me to resume tasks that were paused.

- In `func sceneWillResignActive(_ scene: UIScene)`, I take actions when the scene is about to transition from active to inactive, which could be due to temporary interruptions like an incoming call.

- `func sceneWillEnterForeground(_ scene: UIScene)` I use when the scene returns to the foreground, allowing me to undo changes made when entering the background.

- Finally, `func sceneDidEnterBackground(_ scene: UIScene)` is called when the scene moves to the background, allowing my application to save data, release shared resources, and store scene-specific information to restore its state.

On the other hand, the `AppDelegate` is responsible for managing launch and termination events of the application:

- `func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool` is executed at the application's launch and allows me to customize and configure the application. In this case, my code simply prints "Application did finish launching" and returns `true` to indicate a successful launch.

- `func application(_ application: UIApplication, configurationForConnecting connectingSceneSession: UISceneSession, options: UIScene.ConnectionOptions)` is called when a new scene session is created and allows me to select a scene configuration. My code prints "Application configuring a Scene Session" and returns a default scene configuration.

- `func application(_ application: UIApplication, didDiscardSceneSessions sceneSessions: Set<UISceneSession>)` I use when the user discards a scene session. It allows me to release resources specific to the discarded scenes since they won't be reused. My code prints "Application did discard Scene Sessions."

In summary, these two components, `SceneDelegate` and `AppDelegate`, are essential for controlling the lifecycle of an iOS application, enabling specific actions in response to important events such as scene connections, state transitions, and discarded sessions. The use of print statements in each method is a useful tool for debugging and event tracking.

#### 3 - Model View Controller

##### FavoriteAthlete

https://github.com/Marcoc-rasi/DEVELOPMENT-WITH-SWIF-DATA-COLLECTIONS/assets/51039101/acb1c1c6-ccd8-4798-bff5-cb738b7cd19f

The code consists of three main sections that together form an application for managing athlete information. The first code snippet defines a class called `AthleteTableViewController`, which inherits from `UITableViewController` and is used to display a list of athletes in a table view within an iOS application.

The `AthleteTableViewController` class employs an array called `athletes` to store objects of the `Athlete` structure. This structure, defined in the second code snippet, represents an athlete with properties such as name, age, league, and team. The `Athlete` structure also features a computed property called `description`, which generates a textual description of the athlete.

The application uses three key methods within `AthleteTableViewController` to interact with the table view. The `viewWillAppear` method ensures that the table view is updated before it appears on the screen. Subsequently, the `tableView(_:numberOfRowsInSection:)` and `tableView(_:cellForRowAt:)` methods from the `UITableViewDataSource` protocol are employed to determine the number of rows and how the table view cells should be configured.

Additionally, the `AthleteTableViewController` class contains two actions annotated with `@IBSegueAction`. The first, `addAthlete`, is triggered when adding a new athlete and creates an instance of `AthleteFormViewController` for this purpose. The second, `editAthlete`, is invoked for editing an existing athlete and passes the selected athlete to `AthleteFormViewController` for editing. Finally, the `unwindToAthleteTableViewController` action handles the unwind transition from `AthleteFormViewController` and updates the athlete list accordingly.

The third code snippet defines the `AthleteFormViewController` class, which is used for editing or adding athletes. This view contains text fields for entering athlete information, including name, age, league, and team. The `updateView` function updates these text fields with athlete information if an athlete is provided. The `save` action saves changes or creates a new athlete with the information entered in the text fields.

In summary, this iOS application comprises two view controllers: `AthleteTableViewController`, which displays a list of athletes in a table view, and `AthleteFormViewController`, which allows for adding or editing athletes. The `Athlete` structure represents athlete information, and methods and actions are used to interact with the table view and the editing form. The workflow involves adding, editing, and saving athlete information in an iOS application.

#### 4 - Scroll Views

##### ISpy-Marcocrasi

https://github.com/Marcoc-rasi/DEVELOPMENT-WITH-SWIF-DATA-COLLECTIONS/assets/51039101/8517974f-8ca4-47b8-bac0-2f8846ce4a5a

This code snippet is part of an application that displays an image of a cat and allows zoom and pan operations within the zoomed area.

First, we import the UIKit module, which is crucial for iOS app development. Then, we define a class called `ViewController`, acting as the primary controller for the app's view. The class inherits from `UIViewController` and conforms to the `UIScrollViewDelegate` protocol, indicating that we're enabling manipulation of scroll views.

Within this class, we find two essential properties:
- `scrollView`, which is labeled with `@IBOutlet`, suggesting it refers to a `UIScrollView` object in the user interface. This object serves as a viewport to display the cat image and enables scrolling in case the image is larger than the screen.
- `imageView`, another property labeled with `@IBOutlet`, indicating it refers to a `UIImageView` object in the user interface. This is the cat image to be displayed within the scroll view.

When the view is loaded into memory, the `viewDidLoad` method is executed, setting the `delegate` property of the `scrollView` to be this very instance of `ViewController`. This implies that the `ViewController` class will control the behavior of the scroll view.

The `viewDidAppear` method is called when the view is presented on the screen, and here, we invoke `updateZoomFor(size:)`, passing the current view's size as a parameter. This ensures that the image's zoom is appropriately adjusted to the screen size.

The `viewForZooming(in scrollView: UIScrollView)` method is part of the `UIScrollViewDelegate` protocol and determines that the view to be scaled (zoomed) is the cat image.

Finally, the custom method `updateZoomFor` calculates the scale factors necessary to fit the image within the zoom area. The scale factors are determined based on the image's size (`imageView.bounds`) and the current view's size (`view.bounds`). Then, both the `scrollView.minimumZoomScale` and `scrollView.zoomScale` are set to the minimum value of the scale factors, ensuring the image fits correctly within the scroll view.

In summary, this code configures a scroll view that displays an image of a cat, allowing zoom and pan operations within the zoomed area. The logic within the `ViewController` class ensures that the image fits appropriately on the screen and provides a smooth user experience when interacting with the cat image.

##### ScrollingForm-Marcocrasi

https://github.com/Marcoc-rasi/DEVELOPMENT-WITH-SWIF-DATA-COLLECTIONS/assets/51039101/9c4d3282-49e5-4938-916f-e6b73c1d9284

This Swift code snippet is part of an iOS application and resides within a class named `ViewController`. The purpose of this code is to ensure that, when the keyboard appears or disappears within the application, the view adjusts automatically to keep text input fields visible and accessible.

Within the `ViewController` class, a property called `scrollView` is declared, representing a `UIScrollView` object. This object is used to create a scrollable view in the user interface.

The `viewDidLoad()` method is executed when the view loads. Here, the initial view setup is performed, including the registration of keyboard-related notifications by calling `registerForKeyboardNotifications()`.

The `registerForKeyboardNotifications()` method is responsible for registering two system notifications: one triggered when the keyboard is shown and another when it is hidden. These notifications are crucial for responding to keyboard-related events.

When the keyboard is shown, the `keyboardWasShown(_:)` method is called. In this method, information about the keyboard, such as its size, is obtained, and this information is used to adjust the content of the `scrollView`. The `contentInset` and `scrollIndicatorInsets` properties of the `scrollView` are modified to ensure that text input fields remain visible.

When the keyboard is about to be hidden, the `keyboardWillBeHidden(_)` method is called. In this case, the `contentInset` and `scrollIndicatorInsets` properties of the `scrollView` are reset to their original state, ensuring that the view returns to its normal position.

In summary, this code is essential for ensuring a seamless user experience in an iOS application. When the keyboard is shown, the view automatically adjusts to prevent the keyboard from covering user interface elements. When the keyboard is hidden, the view returns to its original state. This approach enhances usability by allowing users to interact with text input fields conveniently, without keyboard obstructions. The use of system notifications and manipulation of the `scrollView` are key to achieving this behavior.

##### ScrollingChallengeHorizontal

https://github.com/Marcoc-rasi/DEVELOPMENT-WITH-SWIF-DATA-COLLECTIONS/assets/51039101/0f304516-4c40-4e01-a546-606b6ec77faa

An application has been developed to fulfill the challenge of creating a horizontal scroll view that showcases three favorite images. This app features a visually pleasing horizontal scroll view with the user's top three favorite images. Users can easily swipe through these images to enjoy and appreciate the chosen favorites. 

#### 5 - Table Views

##### Meal Tracker - Marcocrasi

https://github.com/Marcoc-rasi/DEVELOPMENT-WITH-SWIF-DATA-COLLECTIONS/assets/51039101/7c0dd144-8529-4008-bd24-9f7aa9157600

The code I've shared represents an application called `Meal Tracker` that uses Swift and the iOS platform to track meals and the foods within them. The application consists of three essential parts: the `Meal` structure, the `Food` structure, and the `FoodTableViewController` class.

The `Meal` structure is used to model information about meals. Each instance of `Meal` has two crucial properties:
- `name`: This property stores the name of the meal, such as "Breakfast," "Lunch," or "Dinner."
- `food`: This property is an array of elements of the `Food` type, representing the foods that are part of that meal.

The `Food` structure is used to model information about individual foods. Each instance of `Food` has two key properties:
- `name`: It stores the name of the food, for example, "Waffles" or "Avocado Toast."
- `description`: It stores a detailed description of the food, such as "A short stack of buttermilk pancakes can be a sweet and filling treat to enjoy any time of day."

The `FoodTableViewController` class is a view controller that inherits from `UITableViewController`. It is responsible for displaying information about meals and foods in a table view. The controller is initialized with a property called `meals`, which contains an array of `Meal` instances representing breakfast, lunch, and dinner. Each meal has a name and a list of associated foods.

The view controller's lifecycle begins with the `viewDidLoad` method, which is used for any initial setup. Subsequently, several methods from the `UITableViewDataSource` protocol are implemented to manage the table view:
- `numberOfSections(in tableView:)` returns the number of sections in the table view, which matches the number of meals.
- `tableView(_:numberOfRowsInSection:)` returns the number of rows in a section, equivalent to the number of foods in a specific meal.
- `tableView(_:cellForRowAt:)` configures each cell in the table view with the name and description of the corresponding food.
- `tableView(_:titleForHeaderInSection:)` provides the title for each section in the table view, which is the meal name.

In summary, this code represents an application that allows tracking of meals and their associated foods. The `Meal` and `Food` structures are used to organize the information, and the `FoodTableViewController` class manages the user interface to display the data in a table view.

##### EmojiDictionary

https://github.com/Marcoc-rasi/DEVELOPMENT-WITH-SWIF-DATA-COLLECTIONS/assets/51039101/01503d52-4ad7-4598-b691-2c7f03e8dc98

Certainly, I'll provide the explanation in English, highlighting important keywords or terms with backticks:

The code is an implementation of a table view is used to display a list of emojis and allows operations like deleting and rearranging items in the list.

The core of the implementation is a class called `EmojiTableViewController` that inherits from `UITableViewController`. In programming terms, "inherits" means that this class inherits properties and methods from the base class `UITableViewController`, which is a pre-defined table view in iOS. This makes it easy to create a custom table view.

Inside this class, an array named `emojis` is declared, containing objects of the `Emoji` structure. In programming, a "structure" is a data type that groups related properties. In this case, `Emoji` is a structure representing an emoji and has four key properties: `symbol`, `name`, `description`, and `usage`. These properties store the emoji's symbol, its name, a description, and its usage, respectively.

The table view is configured in the `viewDidLoad` and `viewWillAppear` methods. In `viewDidLoad`, a "Edit" button is set in the navigation bar, allowing users to edit the list of emojis. Additionally, the `cellLayoutMarginsFollowReadableWidth` property of the table is adjusted to follow the readable content width. This is relevant for right-to-left language design and ensures a proper appearance in different languages.

The table-related methods are necessary to set up and control the table view. The `numberOfSections(in tableView:)` method returns the number of sections in the table, which in this case is 1. "Sections" refer to the division of the table into distinct parts. `tableView(_:numberOfRowsInSection:)` returns the number of rows in section 0, which equals the number of emojis in the array. Each "row" represents an item in the list.

The `tableView(_:cellForRowAt:)` method is crucial for configuring each cell in the table. In this method, four key steps are followed:
1. **Dequeue cell:** This refers to obtaining a cell from the reuse queue, which is an efficient technique to manage cells in the table view.
2. **Fetch model object:** The corresponding emoji is retrieved from the `emojis` array based on the row index.
3. **Configure cell:** The cell is configured with emoji information, including the symbol and description.
4. **Return cell:** Finally, the configured cell is returned.

The `tableView(_:didSelectRowAt:)` method is called when a cell is tapped and displays the symbol of the selected emoji along with its index in the list. This method enables user interaction with the emojis.

Furthermore, methods for editing the table are provided, such as `tableView(_:commit:forRowAt:)` for deleting emojis from the list and `tableView(_:moveRowAt:to:)` for rearranging emojis using drag-and-drop gestures. These methods are essential to provide editing functionality in the table view.

In summary, this code is an implementation of a table view in iOS that displays a list of emojis, allowing for editing and rearranging. The `Emoji` structure is used to organize information for each emoji. The detailed technical explanation provided here covers fundamental aspects of the implementation, including class inheritance, the use of structures to model data, and the configuration of the table view in an iOS application.

#### 6 - Intermediate Table Views

#### Favorite books

https://github.com/Marcoc-rasi/DEVELOPMENT-WITH-SWIF-DATA-COLLECTIONS/assets/51039101/b267f9aa-94b6-4e28-89d8-dca0aa3f1abd

The code provided is a Swift implementation for an iOS application focused on managing books. The `BookTableViewController` class is a subclass of `UITableViewController` and is used to control a table view in the application's user interface. The table view is used to display a list of books, and I am responsible for managing its content and behavior.

Within this class, I declared a property called `books`, which is an array of `Book` objects. This array stores the books that will be displayed in the table view.

I configured standard table view methods such as `numberOfRowsInSection` and `cellForRowAt` to determine how many rows the table view should have and how to display book data in the cells. Additionally, I implemented a `commit editingStyle` method to allow the deletion of books by swiping a cell.

The class also contains methods related to navigation between views. The `prepareForUnwind` method handles the process of saving changes when editing an existing book or adding a new book to the `books` array. The `editBook` method is used to edit an existing book by selecting a row in the table view.

The `BookTableViewCell` class is a subclass of `UITableViewCell` and is used to customize the appearance of cells in the table view, displaying detailed information about a book. Each instance of `BookTableViewCell` contains labels (`UILabels`) to display the book's title, author, genre, and length. The `update(with:)` method is responsible for updating the labels with the relevant book information.

Lastly, the `Book` structure represents a book with properties for the title, author, genre, and length. I also implemented the `CustomStringConvertible` protocol, which allows me to generate a text representation of the book using the `description` property. This property returns a string that includes detailed information about the book, such as the title, author, genre, and length.

In summary, the provided code is a Swift implementation for an iOS book management application. It uses classes and structures to represent books and customize their display in a table view. Table view methods handle data presentation, and the `Book` structure provides a detailed textual description of a book for display. The code also includes logic for editing and navigating between views.

#### EmojiDictionary

https://github.com/Marcoc-rasi/DEVELOPMENT-WITH-SWIF-DATA-COLLECTIONS/assets/51039101/a4e950dc-f27f-4b22-9768-bcd3f9037eb8

In the provided code, an iOS application is created using the UIKit framework to manage a list of emojis with their corresponding properties. The application consists of several interconnected parts to achieve this functionality. Emoji information is stored in instances of the `Emoji` structure, which conforms to the `Codable` protocol.

The `EmojiTableViewController` class is responsible for displaying the list of emojis in a table view. This class inherits from `UITableViewController` and contains a property named `emojis` that stores an array of `Emoji` objects. The table view is configured with the information from these objects, including their symbol, name, description, and usage.

The lifecycle of the table view is controlled in the `viewDidLoad` and `viewWillAppear` methods. The former sets the initial appearance of the view, including configuring the edit button and cell height. The latter method is responsible for reloading data in the table view every time it appears.

The `EmojiTableViewCell` class defines the appearance of the table view cells. It contains text labels to display the symbol, name, and description of each emoji. The `update(with emoji: Emoji)` method customizes a cell with the information of a specific emoji.

The `AddEditEmojiTableViewController` class is used to add or edit emojis. This view contains text fields for the symbol, name, description, and usage of the emoji. The save button's state is automatically updated based on the validity of the data entered in these fields. Additionally, the `containsSingleEmoji(_ textField: UITextField)` method checks if the symbol field contains a single emoji.

Upon selecting the save button, the information is saved in an instance of `Emoji`. The preparation of this information is carried out in the `prepare(for segue: UIStoryboardSegue, sender: Any?)` method. Data flow between the edit view and the list view is managed using the segue identifier `saveUnwind`.

In summary, the code provides an iOS application that allows the management of a list of emojis with operations for adding, editing, and deleting. Emojis are represented using the `Emoji` structure and are displayed in a table view. The edit view ensures the integrity of the data before saving it and communicates changes back to the list view. The code follows best practices for iOS app development and leverages the `Codable` protocol for easy serialization of objects in JSON format.

#### 7 - Saving Data

https://github.com/Marcoc-rasi/DEVELOPMENT-WITH-SWIF-DATA-COLLECTIONS/assets/51039101/8c820d0a-85f2-4a37-9bbb-ea11a038ad3e

##### EmojiDictionary savin data

In the provided code, a set of classes and structures are defined, forming an iOS application for managing and displaying emojis. A detailed explanation of the key parts of the code is as follows:

**`Emoji` Struct:**
A structure called `Emoji` is defined to represent an emoji. This structure contains properties for the "symbol," "name," "description," and "usage" of an emoji. Additionally, a computed property called `archiveURL` is set to determine the location where emojis will be stored in a Property List (plist) file. A static list named `sampleEmojis` is provided, containing example emojis, which is useful for initializing the application with predefined data. Static methods `saveToFile(emojis: [Emoji])` and `loadFromFile()` are also implemented to save and load emojis from a plist file. This ensures data persistence, allowing emojis to be stored locally and retrieved as needed.

**`EmojiTableViewController` Class:**
A class named `EmojiTableViewController` is defined, inheriting from `UITableViewController`. This class is responsible for managing the table view that displays the list of emojis. In its `viewDidLoad` method, it performs initial configurations, such as assigning an edit button to the navigation bar and loading emojis from storage. Additionally, it implements a series of methods related to table management, such as cell updates, emoji deletion, and item reordering.

**`EmojiTableViewCell` Class:**
The `EmojiTableViewCell` class represents a custom cell for the table. It contains labels to display the symbol, name, and description of the emoji. The `update(with emoji: Emoji)` method is responsible for updating the cell's content with emoji information.

**`AddEditEmojiTableViewController` Class:**
The `AddEditEmojiTableViewController` class manages the addition or editing of emojis. This table view contains text fields to enter the symbol, name, description, and usage of the emoji. The enabling of the save button depends on the validation of the text fields and whether a single emoji has been entered in the symbol field. Additionally, this controller allows the unwind transition to save emojis.

Collectively, this code constructs an iOS application that allows users to add, edit, and view emojis. It uses the `Emoji` structures and custom classes to manage data and the user interface. Data persistence is achieved through Property List files, ensuring emojis remain available even after closing the application. This code is presented efficiently and follows iOS development practices by using `UITableViewController`, `UITextField`, and validation methods for a consistent and functional user experience.

#### 8 - System View Controllers

##### HomeFurniture

https://github.com/Marcoc-rasi/DEVELOPMENT-WITH-SWIF-DATA-COLLECTIONS/assets/51039101/33b90da3-60cf-44e3-a59b-4701ee8e28d7

The code consists of three classes within the context of an iOS application written in Swift using the UIKit framework: `Room`, `Furniture`, and `FurnitureDetailViewController`. These classes are designed to model and manage information about rooms, furniture, and furniture details, allowing users to select furniture images and share relevant information. Below are the key functionalities and features of each class.

The `Room` class represents a room and consists of two essential properties:

- `"name"`: Stores the name of the room.
- `"furniture"`: An array of `Furniture` objects representing the collection of furniture items in that room.

The class's initializer allows for the creation of room instances with a specific name and a list of associated furniture. The `Room` class is part of the Swift standard library, and the `Foundation` module is imported to ensure its availability.

The `Furniture` class models an individual piece of furniture and comprises three key attributes:

- `"name"`: Contains the name of the furniture item.
- `"description"`: Stores a detailed description of the furniture.
- `"imageData"` (optional): Represents binary image data associated with the furniture. This property is optional, meaning it can be null, providing flexibility in modeling different pieces of furniture, some with associated images and others without.

The custom initializer for the `Furniture` class allows for the creation of furniture instances with mandatory name and description, and optionally, image data. This provides flexibility when modeling different pieces of furniture, some with images and others without.

The `FurnitureTableViewController` class is a table view controller responsible for displaying information about rooms and their furniture in a user interface. Some key features of this class include:

- The definition of an internal structure named `"PropertyKeys"` that stores a table view cell identifier for later use.
- The `"rooms"` property that stores a list of `Room` instances, each representing a room with its name and associated furniture.
- The implementation of methods from the `UITableViewDataSource` protocol to provide data to the table view, including the number of sections, the number of rows in each section, and the configuration of table cells.
- A `showFurnitureDetail` method that handles displaying furniture details when a cell is selected.

Finally, the `FurnitureDetailViewController` class represents the detail view of a furniture item within the application. This class offers the following key functionalities:

- Allows the user to choose a photo for the furniture, involving the use of a `UIImagePickerController` and the presentation of options to take a photo with the camera or select an image from the device's photo library.
- Provides the ability to share information about the furniture, including its name, description, and photo, through an activity interface (`UIActivityViewController`).

In summary, these classes work together to create an application that enables users to view detailed information about rooms and their furniture, select images for specific furniture items, and share furniture details with other applications. The modularity and flexibility in furniture and room representation facilitate data management in the application.

##### SystemViewControllers-Marcocrasi

https://github.com/Marcoc-rasi/DEVELOPMENT-WITH-SWIF-DATA-COLLECTIONS/assets/51039101/41e84555-bce7-4d11-90f2-236d68524576

The presented code is a view controller (`ViewController`) in a Swift-written iOS application that integrates various key functionalities to interact with the device and perform actions such as sharing images, viewing websites, taking photos, and sending emails.

The `ViewController` class implements three protocols: `UIImagePickerControllerDelegate`, `UINavigationControllerDelegate`, and `MFMailComposeViewControllerDelegate`. These protocols are essential for interacting effectively with the camera, photo album, and email service.

In the "shareButtonTapped" button action, a "UIActivityViewController" is utilized to allow the user to share an image. The activity controller provides an interface that displays available applications for sharing the image, such as "Messages" or "Email."

The "safariButtonTapped" button launches an "SFSafariViewController" that allows users to view a website, in this case, Apple's website. The "SFSafariViewController" is a view controller that provides a web browsing experience without leaving the app.

The "cameraButtonTapped" button displays a "UIImagePickerController" in the form of an action sheet ("UIAlertController"). This controller enables the user to choose between two image sources: "camera" or "photo library." The code configures the controller according to the choice and presents the camera or photo library interface to the user.

The "imagePickerController" method handles the selection of images from the camera or photo library. The selected image is displayed in the image view ("imageView").

Upon tapping the "emailButtonTapped" button, it checks if the device can send emails using "MFMailComposeViewController." This email composition controller is configured with predefined recipient address, subject, and body. If there is an image in the "imageView," it's attached to the email as an attachment.

The "mailComposeController" method is called when the user has finished composing the email and is responsible for dismissing the mail composition controller.

In summary, this code demonstrates an implementation of a user interface that allows sharing images, opening websites, taking photos, or selecting images from the photo library, and sending emails directly from the app. Specific iOS protocols and controllers, such as "UIActivityViewController," "SFSafariViewController," and "MFMailComposeViewController," are crucial for providing these built-in functionalities effectively.

##### Challenge SystemViewControllers-Marcocrasi

https://github.com/Marcoc-rasi/DEVELOPMENT-WITH-SWIF-DATA-COLLECTIONS/assets/51039101/f60566fe-3dd3-4385-9ed7-ce064221724d

The code is part of an iOS project and utilizes the UIKit framework to create a user interface with various buttons, each performing different actions. These actions include sharing an image, opening a website in Safari, taking a photo with the device's camera, sending an email, and sending a text message.

The code begins by importing two essential modules: `SafariServices` for opening Safari within the app and `MessageUI` for sending emails and text messages.

The primary class in the code is called `ViewController`, which inherits from `UIViewController` and implements several protocols, such as `UIImagePickerControllerDelegate`, `UINavigationControllerDelegate`, `MFMailComposeViewControllerDelegate`, and `MFMessageComposeViewControllerDelegate`.

Within this class, there is a property called `imageView`, which is associated with an image view in the user interface. This image view is used to display selected or captured images.

The `viewDidLoad` method is the view's initialization method and doesn't perform any additional actions in this case.

There are several `@IBAction` methods that correspond to the various buttons in the user interface:

- The `shareButtonTapped` method is triggered when the "Share" button is pressed. It checks if an image is present in the `imageView`, and if so, it creates an activity controller (`UIActivityViewController`) that allows users to share the image through various apps and services.

- The `safariButtonTapped` method opens the Safari browser within the app and loads Apple's web page when the "Safari" button is pressed.

- When the "Camera" button is pressed, the `cameraButtonTapped` method is called. It displays an alert controller (`UIAlertController`) that allows the user to select the image source (camera or photo library) and then presents an image picker controller (`UIImagePickerController`) for taking photos or selecting images from the photo library.

- The `imagePickerController(_:didFinishPickingMediaWithInfo:)` function is called when an image is selected or taken with the image picker controller. It updates the `imageView` with the selected image and dismisses the image picker controller.

- The `emailButtonTapped` method is triggered when the "Email" button is pressed. It checks if sending emails is possible and, if so, creates an email controller (`MFMailComposeViewController`) that allows users to send a pre-defined email with an attached image, if available.

- The `mailComposeController(_:didFinishWith:result:error:)` function is called when email composition is completed. It closes the email controller.

- The `messageComposeViewController(_:didFinishWith:)` function is invoked when text message composition is completed, closing the text message controller.

- Finally, the "Message" button triggers the `messageButtonTapped` method, which checks if sending text messages is possible. If it is, a text message controller (`MFMessageComposeViewController`) is created to enable users to send a pre-defined text message to specific recipients.

In summary, this code demonstrates how to use various controllers and iOS functionalities to perform actions like sharing images, opening links in Safari, taking photos, sending emails, and sending text messages within an iOS application. These functions are connected to specific user actions through buttons in the user interface.

#### 9 - Complex Input Screens

##### EmployeeRoster

https://github.com/Marcoc-rasi/DEVELOPMENT-WITH-SWIF-DATA-COLLECTIONS/assets/51039101/5b0e0b60-78bf-404c-a4ec-ee5953774556

The provided code snippet comprises several interconnected components forming an iOS employee tracking application. In this system, various essential programming concepts and patterns are employed, which will be detailed below.

The code consists of three Swift view controllers that interact to manage and display information about employees. These view controllers are:

- `EmployeeTypeTableViewController`: This view controller displays a list of employee types and allows the user to select one. It employs a protocol named `EmployeeTypeTableViewControllerDelegate` to communicate the selected employee type back to the main controller.

- `EmployeeListTableViewController`: It serves as the main controller, presenting a list of employees in a table view. It permits editing, deletion, and viewing of employee details. It utilizes an array of `Employee` to maintain employee data.

- `EmployeeDetailTableViewController`: This view controller is responsible for displaying details of a specific employee, allowing the user to edit and save changes. It also provides an interface for selecting the employee type.

The data model is represented using two structures:

- `EmployeeType`: An enum that enumerates different employee types, including "exempt," "non-exempt," and "part-time." Each enum case has a description that is used to display the employee type in the user interface.

- `Employee`: A structure that models an employee, with properties including the employee's name, date of birth, and employee type (based on the `EmployeeType` enum).

The application flow unfolds as follows:

1. The main controller, `EmployeeListTableViewController`, displays a list of employees in a table view.

2. Tapping an employee cell triggers a navigation action to display the details of that employee in `EmployeeDetailTableViewController`.

3. `EmployeeDetailTableViewController` allows the user to edit the name, date of birth, and employee type of the selected employee. Employee type selection is facilitated through a button that displays a popover table view, `EmployeeTypeTableViewController`.

4. When changes are made in `EmployeeDetailTableViewController`, the user can save or cancel edits. When saving, employee data is updated, and the main controller is notified through the delegate.

5. The `EmployeeType` structure is used to provide a human-readable description of employee types in the user interface, enhancing user understanding.

6. For the date of birth, logic is implemented to set a default date based on the average age of employees, as an additional challenge.

In summary, the code presents a comprehensive implementation of an iOS employee tracking application that utilizes multiple view controllers and a data model to manage and display information about employees, including their name, date of birth, and employee type. Protocols and delegates are employed to communicate changes and selections between the view controllers.

##### Hotel Manzana

https://github.com/Marcoc-rasi/DEVELOPMENT-WITH-SWIF-DATA-COLLECTIONS/assets/51039101/f02be49e-5510-4aca-9e40-26f0313dec20

The provided code consists of a view controller in an iOS application that allows users to manage room reservations at a hotel.

In this view controller, you can find multiple properties and user interface connections (Outlets) representing elements such as text fields, labels, switches, among others. Additionally, properties are defined to track the state of the date picker and the selected room type.

One of the crucial functions of this controller is to calculate and display charges related to the reservation, such as the number of nights, room rate, Wi-Fi fee, and the total amount. This calculation is performed in the `updateChargesSection` method.

The view controller also implements various `@IBAction` methods triggered in response to user actions. For example, when the user changes the text in name fields, adjusts dates in date pickers, or modifies the number of adults or children, the corresponding information is updated in the user interface. Additionally, a method is included to change the state of the Wi-Fi switch.

To ensure the controller is properly configured, the `viewDidLoad` method is used, which sets initial properties and adapts the user interface based on whether it's a new reservation or an existing one. It also allows the user to edit existing reservations, such as changing the room type or stay dates.

Furthermore, visibility and row height of table cells are managed based on the state of date pickers, ensuring an efficient user experience.

When a user selects a date, the date labels display the selection, and if a date picker is hidden, it becomes visible to enable user modifications.

The `selectRoomType` method is responsible for configuring and presenting the room type selection view. This is achieved by implementing the `SelectRoomTypeTableViewControllerDelegate` protocol, allowing notifications when a room type is selected.

In summary, the provided view controller is a vital component of an application that enables users to manage hotel room reservations. It provides an intuitive interface for entering and editing information related to bookings, calculating charges, and adjusting stay dates and room types. Additionally, it facilitates the editing of existing reservations and ensures an efficient and user-friendly experience.

#### Guided Project - List

##### ToDoList-Marcocrasi

https://github.com/Marcoc-rasi/DEVELOPMENT-WITH-SWIF-DATA-COLLECTIONS/assets/51039101/e4f905f2-c3e1-4f0e-84f8-0d33d73b5e8b

In the code, an iOS application is being developed to manage a list of "To-Do" tasks. This application utilizes several classes and structures that work together to enable users to create, view, edit, and delete tasks.

The central class of the application is `ToDoTableViewController`, which inherits from `UITableViewController`. This class serves as the main view controller and is responsible for displaying the list of "To-Do" tasks in a table view. It also implements the `ToDoCellDelegate` protocol to handle specific events from the task cells.

The "To-Do" tasks in the application are represented using the `ToDo` structure. Each task has properties such as a "unique identifier" (UUID) that ensures its uniqueness, a "title" that describes the task, an "isComplete" indicator that shows whether the task is marked as complete, a "due date," and an optional "notes" field related to the task. The `ToDo` structure also provides methods for saving, loading, and comparing tasks.

The `ToDoTableViewController` view controller uses an array of `ToDo` objects to store the "To-Do" tasks. When loading the view, it checks if there are previously saved tasks. If they exist, it loads them; otherwise, it loads sample tasks.

The table view is populated with the "To-Do" tasks and displays relevant information such as the title and completion status. Users can add new tasks by tapping the "add" button or edit existing tasks by selecting a task from the list. Additionally, they can mark tasks as complete or incomplete by tapping a checkmark button.

When a task is edited, the `ToDoDetailTableViewController` view is opened. This view allows the user to enter or modify the task's title, due date, and notes. It also features a checkmark button to toggle the task's completion status. The `ToDoTableViewController` communicates with this view to update or save tasks using the "unwindToToDoList(segue: UIStoryboardSegue)" method.

The custom cell `ToDoCell` is used to display each task in the table view. The cell contains a label to display the task's title and a checkmark button to change the completion status of the task. When the checkmark button is tapped, it notifies the view controller through the `ToDoCellDelegate` protocol.

In summary, the provided code outlines the structure and workflow of an iOS application for managing a list of "To-Do" tasks. Tasks are represented using the `ToDo` structure, and the application employs view controllers and custom cells to allow users to interact with tasks, modify them, and mark them as complete or incomplete. The application also supports saving and loading tasks to maintain a persistent record of them.

### 2 - Working With The Web

#### 3 - Animations

##### Contest

https://github.com/Marcoc-rasi/DEVELOPMENT-WITH-SWIF-DATA-COLLECTIONS/assets/51039101/9a5645bd-ff91-4c91-bf71-bc3f6ddf7379

In this code, a class named `ViewController` is defined, which inherits from `UIViewController.` View Controllers in iOS are responsible for the management of the user interface and view logic.

Within this class, a property named `emailTextField` is declared with the `@IBOutlet` attribute. This attribute signifies that this property is connected to a user interface element in Interface Builder, in this case, a text field.

The `viewDidLoad` method is automatically called when the view is loaded into memory. Currently, this method is empty, but it is used to perform additional configurations in the view, if necessary.

The `enterButtonDidTouchUpInside` method is executed when a button is tapped, in this case, the `Enter` button. Here, a check is performed: if the text field (`emailTextField`) is empty, the `performLabTextFieldShakeAnimation` method is called. Otherwise, a transition to another view is made using `performSegue(withIdentifier:sender:)`.

The `performLabTextFieldShakeAnimation` is a private method that carries out an animation on the text field (`emailTextField`) to simulate a `shake` effect when the field is empty. This animation employs a transformation that shifts the field 20 points to the right and then returns it to its original position. The total duration of the animation is 0.4 seconds, divided into two parts of 0.2 seconds each: 0.2 seconds for the shift and 0.2 seconds for returning to the original position.

Furthermore, an extension named `Challenge Solution` is provided, which defines a method `performChallengeTextFieldShakeAnimation.` This method executes a more intricate animation to simulate a `shake` effect on the text field. `UIView.animateKeyframes` is used to divide the animation into multiple steps or `keyframes.` Each keyframe horizontally shifts the text field and then returns it to its original position. This creates a more elaborate `shaking` effect that repeats several times.

In summary, this code represents a View Controller in an iOS application that performs animations in response to user interaction. The `shake` animation is utilized to indicate an empty text field, and the `Challenge Solution` extension offers a more complex version of the `shake` animation for experimentation or challenge purposes.

##### MusicWireframe

https://github.com/Marcoc-rasi/DEVELOPMENT-WITH-SWIF-DATA-COLLECTIONS/assets/51039101/1b9e7579-1522-42ad-b871-76b810250f4e

The provided code represents a view controller (`ViewController`) in Swift, designed to oversee and control a music playback interface in an application.

The `ViewController class` contains several properties labeled with the `@IBOutlet` notation, which are associated with user interface (GUI) components. These properties include `albumImageView`, `reverseBackground`, `playPauseBackground`, `forwardBackground`, `reverseButton`, `playPauseButton`, and `forwardButton`.

The `playback state` is controlled by the `isPlaying` variable, which determines whether the music is playing (`true`) or paused (`false`). This state is visually reflected through the `playPauseButton`.

Within the `viewDidLoad` method, visual elements are configured, such as the `background buttons` referred to as `reverseBackground`, `playPauseBackground`, and `forwardBackground`. These elements are prepared for the interface by rounding their corners and initially hiding them with an `alpha` value of `0.0`.

The `playPauseButtonTapped` method is triggered when the `play/pause button` (`playPauseButton`) is tapped. If the music is playing (`isPlaying == true`), an `animation` is initiated that restores the album image to its `original size`. If the music is paused (`isPlaying == false`), an animation is executed that `reduces the size of the album image`.

The `touchedUpInside` and `touchedDown` methods are triggered when a button is released or touched, respectively. It is determined which of the buttons was manipulated (forward, `play/pause`, or reverse), and an `animation` affecting the associated visual elements, such as `buttonBackground`, is executed. When releasing the button (`touchedUpInside`), the elements return to their original state. When touching a button (`touchedDown`), visual effects are applied, including an increase in `opacity` and a slight `size reduction` of the button.

In summary, the code presents a view controller that manages a music playback interface, employing animations and visual interactions to enhance the user experience. When interacting with the playback, pause, and navigation buttons, animations are applied to provide visual feedback. The `album image` is also animated based on the playback state, contributing to a more engaging and dynamic user experience.

#### 6 - WWW Concurrency

##### iTunesSearch

https://github.com/Marcoc-rasi/DEVELOPMENT-WITH-SWIF-DATA-COLLECTIONS/assets/51039101/922b230d-9343-46b5-9209-46848229f868

The code architecture comprises an iOS application designed to interact with the iTunes API, thereby obtaining data related to the categories offered by this platform. At the core of this application, the `StoreItemController` class is defined to manage communication with iTunes web services for searching store items and loading images associated with these items.

Two key methods in this class are `fetchItems(matching query:)` and `fetchImage(from url:)`. The former is used to perform searches in the online store by establishing communication with the iTunes API through HTTP requests. The latter method, `fetchImage`, is employed to load images from URLs provided by the iTunes API. Both methods are designed to handle specific errors using an enumeration called `StoreItemError`. Types of errors that can be managed include the absence of found items and missing image data. This error handling approach provides precise control over potential issues that may arise during interaction with iTunes web services.

The `StoreItem` structure represents individual store items related to iTunes categories. This structure conforms to the `Codable` protocol, enabling it to be encoded and decoded to and from JSON format. The structure includes properties such as name, artist, type, description, and the item's image URL. Its flexibility is evident in its ability to adapt to various data formats provided by the iTunes API.

To manage the encoding and decoding of `StoreItem` objects from JSON, the `CodingKeys` and `AdditionalKeys` enumerations are used. These enumerations allow mapping Swift properties to specific keys present in the JSON returned by the iTunes API. The custom `init(from decoder:)` method is responsible for decoding `StoreItem` objects from a `Decoder` object, ensuring that the item's information is accurately extracted, even when the description of the item is located in different locations within the JSON provided by the iTunes API. The `StoreItem` structure serves as an in-memory representation of store items, and its versatility facilitates the handling of various data formats from the iTunes API.

The `SearchResponse` structure acts as a container for the results of searches conducted through the iTunes API. Within it, there is an array of `StoreItem` objects representing the items found during a search. This structure plays a crucial role in deserializing the JSON response obtained from the iTunes API and converting this data into Swift objects that can be manipulated by the application.

The `ItemCell` class is responsible for customizing the appearance and content of cells in a table view. This customization is achieved by implementing the `updateConfiguration(using state:)` method, which is automatically called to update the cell's configuration based on its state and the data it should display. Cell properties such as `name`, `artist`, and `artworkImage` are configured to trigger configuration updates whenever their values change. Within the `updateConfiguration` method, a configuration is created based on the cell's default configuration. Subsequently, the text and image values of this configuration are set using data provided by the cell's properties. This allows the cell to efficiently display the name, artist, and an image related to the store item. In case an image is not provided, a default image is displayed, along with its symbol and tint configuration.

In summary, the code in question consists of various components aimed at interacting with the iTunes API. These components include a table view controller (`StoreItemListTableViewController`), a store item controller (`StoreItemController`), data structures for representing items and search responses (`StoreItem` and `SearchResponse`), and a custom cell (`ItemCell`) designed to display information related to iTunes categories in a table view. The modularity and adaptability of this architecture enable effective interaction with web services, data management, and the presentation of store items in an iOS application, offering flexible and efficient organization.

##### SpacePhoto

https://github.com/Marcoc-rasi/DEVELOPMENT-WITH-SWIF-DATA-COLLECTIONS/assets/51039101/e2749e6a-cb6a-4145-b3ff-37bf23009413

The provided code consists of three related components: `ViewController`, `PhotoInfoController`, and `PhotoInfo`. These components work together to retrieve information and an image of a space photo from NASA's API and display it in an iOS application. Here's a detailed technical explanation of how these parts function and relate to each other.

First and foremost, the `PhotoInfoController` class is responsible for interacting with NASA's API. This class implements two asynchronous functions for fetching information and an image of the space photo. These functions handle errors and use the `async` annotation to indicate they are asynchronous and can await the completion of network operations.

The `fetchPhotoInfo` function constructs a URL for the request to NASA's API. It then makes an asynchronous HTTP request using `URLSession` to fetch JSON data containing information about the space photo. It ensures the response is valid by checking the HTTP status code. It proceeds to decode the JSON data into an instance of the `PhotoInfo` structure using `JSONDecoder`.

The `fetchImage(from url: URL)` function is used to retrieve the image associated with the space photo. Similar to `fetchPhotoInfo`, it makes an asynchronous HTTP request to get image data from the provided URL. It once again verifies the response, and if it's valid, it creates a `UIImage` instance from the image data.

The `PhotoInfo` class is a data model used to represent information about a space photo. It has properties for storing the title, description, image URL, and copyright information for the photo. It is implemented with conformity to the `Codable` protocol, allowing it to be encoded and decoded to JSON or plist formats. Additionally, an enum named `CodingKeys` is used to establish custom mappings between property names in the structure and keys in NASA's API JSON.

The `ViewController` class serves as the main view controller of the application. In the `viewDidLoad` method, initial UI setup is performed. The `photoInfoController` property is initialized to interact with the API, and asynchronous tasks are initiated to retrieve space photo information and its associated image. The `@MainActor` annotation is used to ensure that UI updates are performed on the main thread.

In case of success, the photo's information and image are updated in the UI using the `updateUI(with photoInfo: PhotoInfo)` method. If an error occurs, the `updateUI(with error: Error)` method is called to handle it and display an error message in the UI.

In summary, this code, in the passive voice, allows the iOS application to interact with NASA's API to obtain information and an image of space photos, and then present this data in the user interface. The `PhotoInfoController` and `PhotoInfo` classes play a critical role in fetching and representing the data, while the `ViewController` class coordinates the interaction and presents the results in the UI. The code employs asynchronous programming and error handling to ensure smooth operation and a responsive user experience.

#### Guided Project - Restaurant

##### OrderApp

https://github.com/Marcoc-rasi/DEVELOPMENT-WITH-SWIF-DATA-COLLECTIONS/assets/51039101/a3f1fae6-9202-4bbb-9f21-0120330334af

The provided code consists of several parts that make up an iOS application for managing a restaurant menu. The application allows users to view available categories, select a category to explore menu items, and place orders.

Firstly, essential data structures to represent the menu and orders are defined. The `MenuItem` structure contains details about a menu item, such as its name, price, and image URL. The `Codable` protocol is used to facilitate the conversion between Swift objects and JSON representations. The `MenuResponse` structure is responsible for deserializing the JSON menu response, while `Order` keeps track of user-selected items in their order.

The application's main controller, `MenuController`, centralizes operations related to the menu. It includes several asynchronous methods to perform various tasks:

- `fetchCategories()`: Retrieves available categories from the server and returns them as an array of strings. `URLSession` is used for network requests, and `JSONDecoder` for deserialization.

- `fetchMenuItems(forCategory categoryName)`: Retrieves menu items for a specific category and returns them as an array of `MenuItem` objects. Similar to the previous method, it uses `URLSession` and `JSONDecoder` for communication and deserialization.

- `submitOrder(forMenuIDs menuIDs)`: Sends an order to the server with a list of selected menu item IDs and returns the estimated time needed to prepare the order. This involves constructing an HTTP POST request with `URLRequest` and using `JSONEncoder` to serialize the order data.

- `fetchImage(from url)`: Fetches an image from a given URL and returns it as a `UIImage` object. `URLSession` is used to download the image, and the HTTP response status is checked.

The controller also defines the `orderUpdatedNotification` to inform other parts of the application about changes in the menu order. The shared instance of `MenuController` (`shared`) is used throughout the application to access the controller's functionalities.

The application consists of multiple views. The `CategoryTableViewController` class is responsible for displaying available categories in a table view. When the view loads, it performs an asynchronous operation to obtain the categories using `MenuController.shared.fetchCategories()`. The results are reflected in the user interface by calling the `updateUI(with categories)` method.

When the user selects a category, a transition to the corresponding menu item table view, `MenuTableViewController`, is initiated. The `CategoryTableViewController` class also defines the standard table view methods to configure the structure and behavior of the table, including cell configuration.

The `MenuItemCell` class customizes the appearance of menu item cells in table views. It uses observed properties to detect changes in data and the `updateConfiguration(using state: UICellConfigurationState)` method to visually update cells with name, price, and optionally an image.

Finally, the `OrderConfirmationViewController` class displays an order confirmation with the estimated preparation time.

In summary, the code presents an iOS application that uses asynchronous programming and `Codable` data structures to manage a restaurant menu. The main controller, `MenuController`, coordinates data retrieval, order placement, and image retrieval. Each view is responsible for displaying specific information, such as categories, menu items, and order confirmations, with detailed cell appearance customization via `MenuItemCell`.

##### OrderApp Extension - State Restoration

https://github.com/Marcoc-rasi/DEVELOPMENT-WITH-SWIF-DATA-COLLECTIONS/assets/51039101/ac873bab-5576-48a7-ae96-808a1099f464

The provided code focuses on an iOS application for managing a restaurant menu and placing orders. The overall structure of the code encompasses several key areas, all controlled by the `MenuController` class. This class serves as the central controller for the application, coordinating data retrieval, UI updates, and order management. Here are the key parts of the code:

First, several data structures are defined to represent fundamental elements of the application:
- The `MenuItem` structure models a menu item and includes properties such as a unique identifier, name, description, price, category, and an image URL. It uses the `Codable` protocol for data encoding and decoding, allowing easy serialization and deserialization of `MenuItem` objects.
- The `MenuResponse` structure represents a response containing an array of `MenuItem` elements. This is useful for decoding the JSON response from the restaurant's menu.
- The `CategoriesResponse` structure is responsible for decoding the JSON response containing available menu categories.
- The `OrderResponse` structure is used to decode the response of an order, including the estimated preparation time. It utilizes key mapping through `CodingKeys` to match property names in the JSON data.

The `MenuController` class plays a crucial role in the application's logic. Some key aspects include:
- Error handling: The class defines a `MenuControllerError` enumeration that encapsulates possible errors, providing localized error messages.
- Order update notification: When the order is updated, an `orderUpdatedNotification` is sent to inform other parts of the application.
- User activity management: An instance of `NSUserActivity` is used to track the application's state, including the current category, menu item, and the current order. This allows for state restoration.

The `MenuController` class also offers a set of asynchronous methods for interacting with the server:
- `fetchCategories()`: Retrieves available menu categories via an HTTP request and decodes the response into an array of strings.
- `fetchMenuItems(forCategory categoryName)`: Fetches menu items for a specific category. This involves constructing the URL and decoding the JSON response.
- `submitOrder(forMenuIDs menuIDs)`: Submits an order with a list of menu item identifiers and receives the estimated preparation time as a response. The request is made as a POST operation with JSON data.
- `fetchImage(from url)`: Downloads an image from a URL and converts it into a `UIImage` object.

Finally, the `CategoryTableViewController`, `MenuTableViewController`, `MenuItemDetailViewController`, and `OrderTableViewController` classes are view controllers responsible for displaying the user interface and managing user navigation within the application. They use asynchronous methods to retrieve data from the server and update the user interface according to categories, menu items, and orders.

Collectively, this code provides a robust foundation for a restaurant application that allows users to navigate the menu, place orders, and keep track of their order's status. The separation of responsibilities between classes and error handling makes the application robust and easy to maintain.

### 3 - Advanced Data Display

#### 1 - Collection Views#####

##### EmojiDictionary

https://github.com/Marcoc-rasi/DEVELOPMENT-WITH-SWIF-DATA-COLLECTIONS/assets/51039101/9c7f8d0e-dc5e-48d4-a84f-30aa9a830c2d

The provided code, spanning multiple interconnected parts, creates an iOS emoji dictionary application. First and foremost, there is the `Emoji` struct, marked as "Codable," to represent an emoji. This struct stores four essential attributes: `symbol`, `name`, `description`, and `usage.` Conforming to "Codable" allows for easy encoding and decoding of emojis in JSON format, simplifying their storage and transmission in an iOS application.

The `EmojiCollectionViewController` class, derived from `UICollectionViewController`, controls the collection view displaying emojis. By configuring the collection view layout using objects like `NSCollectionLayoutItem`, `NSCollectionLayoutGroup`, and `NSCollectionLayoutSection`, the desired appearance is achieved. Loading of emojis occurs during the initialization of the collection view and updates every time it appears on the screen.

The `EmojiCollectionViewCell` class customizes the collection view cells to present emojis. Its labels, tagged with "@IBOutlet," display the `symbol`, `name`, and `description` of the emoji. The `update(with emoji)` function takes care of correctly reflecting these attributes in the cells.

On the other hand, the `AddEditEmojiTableViewController` class is used to add or edit emojis in a table. Text fields, such as `symbolTextField`, `nameTextField`, `descriptionTextField`, and `usageTextField`, are used to input or modify emoji details. Enabling the save button is controlled through the `updateSaveButtonState` function, which checks the suitability of the entered data, including the presence of a single `emoji` in `symbolTextField.` The `textEditingChanged` function updates the save button state in response to changes in the text fields. Lastly, the class prepares emoji information for subsequent storage or updates in the `prepare(for segue: UIStoryboardSegue, sender: Any?).`

In summary, these code pieces enable users to view, add, and modify emojis in the user interface of an iOS application. The structs and classes are meticulously designed to provide a comprehensive experience in emoji management within the application. Conformance to "Codable" facilitates emoji data manipulation, while the `EmojiCollectionViewController` and `AddEditEmojiTableViewController` classes handle emoji presentation and editing in the collection view and the table, respectively. The `EmojiCollectionViewCell` class customizes the visual appearance of emojis in the collection view, ensuring their proper display. Interaction and application logic are implemented consistently throughout the code, delivering an integrated experience in emoji management within the application.

##### BasicCollectionView

https://github.com/Marcoc-rasi/DEVELOPMENT-WITH-SWIF-DATA-COLLECTIONS/assets/51039101/94731158-fbe2-4c64-877f-5708b126af51

The provided code is an implementation of a collection view controller in an iOS application. In this code, a `class` named `BasicCollectionViewController` is defined, which inherits from the `UICollectionViewController` class. This `class` is responsible for being managed by a collection view in the user interface.

The collection view is configured to display a list of `state names` in the United States, which are stored in a `private constant` called `items`. This constant contains an array of strings that represents the `state names`.

The `class` `BasicCollectionViewCell` is used to customize the appearance of the cells in the collection view. This `class` is a subclass of `UICollectionViewCell` and contains a property called `label`, which is an instance of the `UILabel` class. The `label` is declared as an `interface outlet` using the `@IBOutlet` attribute, suggesting that it will be connected to a `label` in the user interface file.

In the `viewDidLoad` method of the `BasicCollectionViewController` `class`, the layout of the collection view is configured using a method called `generateLayout`. The layout of the collection view is set using a `UICollectionViewCompositionalLayout`, which specifies the structure of the view, including `items`, `groups`, and `sections`. In this case, a layout with a single column and fixed-height cells is created.

The `numberOfItemsInSection` method is used to determine the `number of items` to be displayed in the collection view. It returns the `number of items` in the `items` array.

The `cellForItemAt` method is responsible for providing the cells to be displayed in the collection view. A reusable cell identified by `reuseIdentifier` is obtained, and the `text` from the `items` array is assigned to the `text` property of the `label` in the custom cell.

In summary, this code creates a collection view that displays a list of `state names` in custom cells. Customization of the cells is achieved through the `BasicCollectionViewCell` `class`, which contains a `label` to display the text. The structure of the collection view is defined in the `generateLayout` method, and a `UICollectionViewCompositionalLayout` is used to apply the layout.

#### 2 - Swift Generics

##### Life-formSearch

https://github.com/Marcoc-rasi/DEVELOPMENT-WITH-SWIF-DATA-COLLECTIONS/assets/51039101/8552000d-9ec3-4637-8f35-e64546a4e3ba

The `structures` and `classes` provided have been designed to handle network requests and decode responses in an application that interacts with the Encyclopedia of Life (EOL) API. These components are fundamental for obtaining and manipulating biological data within the application.

First, `structures` have been defined to represent data related to objects in EOL. The `EOLItem structure` encapsulates essential information about an object, such as its "common name," "scientific name," and "unique identifier." In particular, the `commonName` and `scientificName` properties are used to describe the common and scientific names of the object, respectively. Additionally, `id` is used to uniquely identify the object.

On the other hand, the `SearchResponse structure` serves to encapsulate a search response, which consists of a list of `EOLItem` objects. This structure is crucial for the application, as it stores the results of searches conducted on EOL.

The `EOLController class` plays a central role in the application as it acts as a network request controller. The implementation of this controller follows a Singleton pattern, meaning it provides a single global instance accessible throughout the application. This instance is accessible through the static property `shared`. The controller offers a method called `sendRequest` that allows for sending network requests asynchronously and handling the responses.

The `sendRequest method` is adapted to work with types that conform to the `APIRequest protocol.` This protocol defines two key requirements: `urlRequest` and `decodeResponse.` The former is responsible for constructing the URL request based on the specific data of each request, and the latter is used to decode the response of the request into a specific type. The implementation of `decodeResponse` depends on the nature of the request and the expected response type.

The controller also includes an extension of the `Data structure` that provides the capability to convert JSON data into a readable and formatted string. This is highly useful for debugging, as it allows for visualizing the structure of JSON response data.

Furthermore, `structures` representing specific requests to the EOL API have been defined. Each request `structure`, such as `EOLSearchAPIRequest,` `EOLItemDetailAPIRequest,` `EOLHierarchyAPIRequest,` and `EOLImageAPIRequest,` implements the `APIRequest protocol` with the aim of constructing specific requests and decoding corresponding responses.

In summary, the provided code comprises `structures` and `classes` that enable interaction with the Encyclopedia of Life API. These components are crucial for making network requests, obtaining data related to biological objects, and decoding responses for further manipulation within the application. The implementation is designed to be efficient and scalable, facilitating the incorporation of new functionalities related to obtaining biological information.

#### 3 - Dynamic Data

##### iTunesSearch

https://github.com/Marcoc-rasi/DEVELOPMENT-WITH-SWIF-DATA-COLLECTIONS/assets/51039101/c0c8e6cc-2217-428a-9aaa-f01512f5123c

The code presents a set of classes and structures designed for implementing an iOS application for searching and displaying items from a store, possibly linked to the iTunes store. Several key components in this code stand out, all contributing to the overall functionality of the application.

Firstly, the `StoreItemListTableViewController` class is defined, inheriting from `UITableViewController`. This class handles the logic related to displaying a list of items in a table. The `tableView(_ tableView: UITableView, didSelectRowAt indexPath: IndexPath)` method is used to manage the selection of a row in the table and to deselect it with animation.

The `StoreItemController` class is crucial in obtaining data and managing images for store items. It contains a set of asynchronous methods to interact with a web API and retrieve information, as well as images associated with store items. Custom errors are defined in the `StoreItemError` enumeration to handle situations where items cannot be found or image information is missing.

In the code, the `UISearchResultsUpdating` protocol is used, and the `StoreItemContainerViewController` class is defined. This class, inheriting from `UIViewController`, serves as the main controller that manages the user interface for searching and displaying store items. Within the class, views are configured, including a table view and a collection view, along with a search controller (`UISearchController`) that allows users to search for items in the store.

Data sources (`tableViewDataSource` and `collectionViewDataSource`) are defined for the table view and the collection view, respectively, and are kept in sync with updated data. Asynchronous tasks for loading images and canceling ongoing tasks are managed, ensuring efficient application performance.

The `StoreItem` class is a structure that represents a store item and is used to decode item information obtained through a network request. The use of `Codable` allows for mapping JSON keys to structure properties, and a custom initializer is provided to handle cases where not all fields are present in the JSON data.

The `SearchResponse` structure is used to represent the response from a search, which is an array of store items. Both the `StoreItem` and `SearchResponse` structures are crucial for processing data related to store items in the application.

Finally, the `ItemTableViewCell` and `ItemCollectionViewCell` classes are defined, which are custom cells used to display store item information in a table view and a collection view, respectively. Both classes inherit from standard cells and conform to the `ItemDisplaying` protocol. The protocol defines properties used to display item information, such as the title, details, and the image.

Within the extensions of these classes, the `configure(for item: StoreItem, storeItemController: StoreItemController) async` method is implemented, which is responsible for configuring the cell with item information and managing the asynchronous downloading of images. This method is essential for efficiently displaying data in custom cells.

Together, these classes and structures form the foundation of an application that allows users to search and view store items, with the ability to load images and efficiently manage asynchronous tasks. The code provides a solid structure for implementing this functionality, covering data management through to user interface presentation.

##### BasicCollectionView

https://github.com/Marcoc-rasi/DEVELOPMENT-WITH-SWIF-DATA-COLLECTIONS/assets/51039101/d5060751-01d6-4e4a-ab84-eb78139b11b9

In the provided code snippet, an implementation of a collection view (UICollectionView) in an iOS development environment using the Swift language is presented. This collection view displays a list of United States states and provides real-time search functionality.

The United States states are defined as a constant array named `items`, which contains all the state names. This is relevant as the data is based on this array and is used for both searching and displaying within the collection view.

A class named `BasicCollectionViewController` has been created, which inherits from `UICollectionViewController` and adopts the `UISearchResultsUpdating` protocol. In this class, key functionalities are implemented, such as search bar management and data presentation within the collection view.

The search bar is managed by a search controller named `searchController`, configured not to obscure the background during result presentation. This is crucial to ensure that search results are visible to the user. Furthermore, the option to keep the search bar visible even when the user scrolls the collection view is enabled (`navigationItem.hidesSearchBarWhenScrolling = false`).

The `createDataSource` method is responsible for setting up a `dataSource` object of type `UICollectionViewDiffableDataSource` to manage the data in the collection view. This is relevant for presenting the elements within the collection view.

The `updateSearchResults` function is executed whenever a search is performed. Search results are filtered based on the text entered into the search bar and applied to the collection view. This update is done with animation to provide a smooth user experience.

The layout of the collection view is defined in the `generateLayout` method. In this layout, the size of items, spacing between them, and other visual aspects are defined. This layout adapts to the content of the collection view and ensures that items are displayed appropriately.

Finally, an additional class named `BasicCollectionViewCell` is defined, which inherits from `UICollectionViewCell`. This class contains a label (`label`) used to display the text of the states in each cell of the collection view. The `label` property is annotated with the `@IBOutlet` attribute, allowing it to be connected to a label in the user interface. This is crucial for customizing the appearance of cells in the collection view.

In summary, the provided code creates an iOS collection view that displays a list of United States states and allows users to search for specific states. The implementation is based on search bar configuration, data management, and customization of the collection view cells. Data is stored in a constant array, filtered based on the search, and efficiently presented within the collection view.

#### 4 - Compositional Layout

#####  Compositional Layout lab

https://github.com/Marcoc-rasi/DEVELOPMENT-WITH-SWIF-DATA-COLLECTIONS/assets/51039101/089578a6-0465-4fc8-ad0d-20643a5cf940

The provided code comprises several components that come together to create an application for managing a collection of emojis. The application is composed of three main classes: `EmojiCollectionViewHeader`, `EmojiCollectionViewController`, and `AddEditEmojiTableViewController`. It also utilizes two structures, `Emoji` and `Section`, to model and organize emojis. Below, we will explain how these parts combine to create the overall functionality of the application.

Firstly, the `Emoji` structure is defined. This structure represents an emoji and stores its core attributes such as the "symbol," "name," "description," and "usage." Additionally, a computed property called "sectionTitle" is dynamically calculated and used to organize emojis into sections based on the initial letter of their names.

The `Section` structure is employed to group emojis into sections with a "title" that identifies the section.

Next, the `EmojiCollectionViewHeader` class is implemented, which extends `UICollectionReusableView`. This class is responsible for creating headers with visual effects for each section in the emoji collection view. The `EmojiCollectionViewHeader` class includes a `UILabel` named "titleLabel" that displays the section's title.

The main class of the application is `EmojiCollectionViewController`, which is a view controller inheriting from `UICollectionViewController`. This class manages the collection view that displays the emojis. The controller is initialized with a set of predefined emojis, which are stored in an array. The collection view is organized based on the current layout, which can be either a "grid" or a "column."

The collection view employs two different layouts generated by the `generateGridLayout` and `generateColumnLayout` methods. These methods configure the structure of the collection view, setting up items, groups, and sections, as well as margins and spacing between items.

Emoji editing is handled through the `AddEditEmojiTableViewController` class. This class allows users to add new emojis or edit existing ones. The text fields in this view correspond to the emoji attributes, such as "symbol," "name," "description," and "usage." The "Save" button is automatically enabled or disabled based on certain conditions, such as the presence of a single emoji in the symbol field and the non-empty state of the text fields.

Additionally, the `textEditingChanged` function is implemented to track changes in the text fields and update the state of the "Save" button.

The application also allows users to delete emojis via a contextual menu, configured in the `contextMenuConfigurationForItemAt` method. Emoji deletion is performed in the `deleteEmoji` method.

In summary, the application manages a collection of emojis in a collection view, organizes emojis into sections, enables the addition and editing of emojis, and provides the option to delete emojis via a contextual menu. The data structure is based on the `Emoji` and `Section` classes, and the user interface is controlled through the `EmojiCollectionViewController` and `AddEditEmojiTableViewController` classes.

#### 5 - Advanced Layout

##### iTunesSearch

https://github.com/Marcoc-rasi/DEVELOPMENT-WITH-SWIF-DATA-COLLECTIONS/assets/51039101/2124db42-8144-4aa0-a9ea-0237a9e1212c

The provided code refers to a set of classes and structures in an iOS application used to display store items in both a table view and a collection view. These classes and structures work together to enable searching and displaying store items based on various search categories. Below is a technical explanation of how this code works and how the different parts are interconnected:

The entry point of the application is a view controller called `StoreItemContainerViewController`. This view controller contains a search bar that allows users to search for items in the store. It also contains two containers, one for a table view and another for a collection view, which are used to display search results.

The code starts by defining an enum called `SearchScope`. This enum represents the different search scopes available in the application, such as "Movies," "Music," "Apps," and "Books." Each scope has a descriptive title and an associated media type. This information is used to filter search results.

Next, the `StoreItem` and `SearchResponse` structures are defined. The `StoreItem` structure represents a store item and includes information like the name, artist, type, description, and image URL. Conforming to the `Codable` protocol facilitates the encoding and decoding of these items to and from JSON. The `SearchResponse` structure is used to represent search responses and contains an array of store items.

In the code, there are two types of custom cells: `ItemTableViewCell` and `ItemCollectionViewCell`. Both cells implement the `ItemDisplaying` protocol, which defines required properties for displaying store items, including an image view, a title label, and a detail label. The cells are used to display items in the table view and collection view.

The implementation of the `ItemDisplaying` protocol is found in an extension that provides a method called `configure(for:storeItemController:)`. This method is responsible for configuring the cell with data from a store item and handles the loading of the item's image using a controller named `StoreItemController`. In case of an error while loading the image, appropriate exceptions are handled.

The `StoreItemController` class is responsible for making search requests and downloading images from store item URLs. It contains asynchronous methods for searching store items and loading images from URLs. Additionally, it defines an enum called `StoreItemError` that represents possible errors related to searching and loading images.

The `StoreItemContainerViewController` is the central point of the application and is responsible for coordinating the search and display of store items. It uses a search controller (`UISearchController`) to enable users to search for items. When changing the search scope, it switches between the table view and the collection view to display the corresponding results.

In summary, this code provides a complete infrastructure for searching and displaying store items in an iOS application. It employs a modular design with custom cells and a central controller to coordinate the search and display of items. Structures and enums are used to represent crucial data and settings, and asynchronous concurrency is leveraged to improve application responsiveness during search and image loading.

##### AppStoreLayout

https://github.com/Marcoc-rasi/DEVELOPMENT-WITH-SWIF-DATA-COLLECTIONS/assets/51039101/ac8b5e34-d34b-477d-a3a9-22c653da83c8

The code is composed of multiple classes and structures in the Swift programming language, and it uses the iOS UIKit framework to create a user interface. The primary purpose of the code is to define the appearance and behavior of a collection view that displays a list of apps and categories from an app store.

- **`App` and `StoreCategory`**: These two structures define the data models for apps and store categories. Each `App` instance contains information about an app, such as title, subtitle, price, and a possible promotional headline. Apps also have a random color for their visual representation. On the other hand, categories are represented by a name and a random color.

- **`Item`**: The `Item` enumeration is used to represent both apps and categories. This structure allows for storing objects of type `App` or `StoreCategory`. It also provides methods to access specific data for an app or category, as appropriate.

- **`PromotedAppCollectionViewCell` and `StandardAppCollectionViewCell`**: These classes define custom cells for the collection view that display apps. `PromotedAppCollectionViewCell` cells are designed to highlight promoted apps, featuring headers, titles, subtitles, and app images. `StandardAppCollectionViewCell` cells present standard apps with titles, subtitles, and images. Additionally, these cells can display a bottom line to separate the cells in the collection view.

- **`CategoryCollectionViewCell`**: This class defines a custom cell for displaying categories in the collection view. Each cell contains a representative category image, a title, and a possible bottom line. Category images and titles are configured based on the corresponding category.

- **`SectionHeaderView` and `LineView`**: These classes represent header views and horizontal lines used in the collection view. `SectionHeaderView` displays a title and a "See All" button in a horizontal layout. `LineView` displays horizontal gray lines used to separate sections in the collection view.

- **`ViewController`**: The `ViewController` class is the main view controller that manages the collection view and its data. In `ViewController`, the collection view is configured, and custom cells, headers, and lines are registered. Additionally, the layout of the collection view, how sections are organized, and how data is displayed are defined. The collection view's data controller is configured to provide and update data as you scroll through the collection view.

Overall, the code focuses on creating a highly customized collection view that displays apps and categories from an app store. Each user interface component is tailored to its specific function, and custom cells and header/views are used to achieve the desired presentation. The `App` and `StoreCategory` structures are used to store app and category data, and the `Item` enumeration provides a unified way to represent this data in the collection view.

#### 6 - Local Notifications

##### BillManager

https://github.com/Marcoc-rasi/DEVELOPMENT-WITH-SWIF-DATA-COLLECTIONS/assets/51039101/5f7e1d12-48d5-433c-90e4-c9fe5686ebfa

The provided code pertains to an application called "BillManager" and consists of various sections that work together to manage bills. The application focuses on managing billing details, including reminders and notifications. Here's a continuous explanation of the code, highlighting key aspects:

**Core Data Model**:
- The core logic of the application is found in the `Bill` struct. Each instance of `Bill` represents a bill and contains attributes such as the amount, due date, notification identifier, paid date, payee, and reminder date.

**Functionality Extensions**:
- In the "Bill+Extras.swift" file, a series of extensions for the `Bill` struct are defined, adding additional functionality related to notifications, reminders, and date formatting.

**Scheduling Reminders**:
- The `scheduleReminder(on date: Date, completion: @escaping (Bill) ->())` function allows scheduling a reminder for a bill on a specified date. This is done using the iOS `UserNotifications` framework. It checks if the app has permissions to send notifications before scheduling a reminder.

**Removing Reminders**:
- The `removeReminder()` function deletes any previously scheduled reminder for a bill. This involves removing the pending notification request and clearing the `notificationID` and `remindDate` properties of the bill.

**Notification Permission Management**:
- The `authorizeIfNeeded(completion: @escaping (Bool) -> ())` function checks if the app has permissions to send notifications. Depending on the permission status, it may request authorization from the user and calls the completion handler with a boolean value indicating whether permissions were granted.

**Central Data Model (Database)**:
- The `Database` class serves as a central data store for bills. It allows adding, updating, deleting, and retrieving bills and maintains them in an in-memory dictionary.

**Data Persistence**:
- Bills are stored in a JSON file in the app's document directory. Loading and saving bills are handled through the `loadBills()` and `saveBills(_ bills: [UUID:Bill])` functions, respectively.

**Update Notifications**:
- The `Database` class emits a custom notification named `billUpdatedNotification` when changes to bills occur. This allows other parts of the app to be informed of updates.

**Bill Comparison**:
- Bills can be compared and sorted based on their due date and amount. The implementation is done in the `Bill` extension.

**User Interface (UI)**:
- The code does not include the implementation of the user interface itself, but it assumes the existence of a UI where users can view and edit bills.

Collectively, this code creates an application for managing bills, enabling users to add, edit, and schedule reminders for their bills. Additionally, it takes care of data persistence and the management of bill-related notifications. The extensions provide additional functionality for efficient bill management.

##### Alarm

https://github.com/Marcoc-rasi/DEVELOPMENT-WITH-SWIF-DATA-COLLECTIONS/assets/51039101/16cbfcf3-e26a-4535-8a5a-c2500bf6f75f

The provided code focuses on managing alarms and notifications in an iOS application. The central structure involved is named `Alarm`. This structure represents an alarm and encompasses various key functionalities.

**Custom Notification:**
The code defines a custom notification called `alarmUpdated`, which is used to inform other parts of the application about updates in scheduled alarms. The notification is defined as `static let alarmUpdated = Notification.Name("alarmUpdated")`.

**The `Alarm` Structure:**
The `Alarm` structure encapsulates the logic for scheduling and unscheduling alarms, as well as notification authorization. It includes the following important properties and methods:

- `notificationId`: A private property that stores a unique identifier for the notification associated with the alarm.
- `date`: A property that stores the date and time of the alarm.
- `init(date: Date, notificationId: String?)`: An initializer that creates an instance of `Alarm` with a date and a custom notification identifier (generating a UUID if not provided).
- `schedule(completion: @escaping (Bool) -> ())`: This method schedules the alarm's notification. It checks notification authorization, configures the notification content, and schedules the notification with a trigger based on the alarm's date and time.
- `unschedule()`: This method cancels the alarm's notification.
- `authorizeIfNeeded(completion: @escaping (Bool) -> ())`: It checks if the application has permission to send notifications and requests permission if necessary.

**Encoding and Decoding:**
The code extends the `Alarm` structure to be `Codable`, allowing instances of `Alarm` to be encoded and decoded. The extension includes static properties like `notificationCategoryId` and `snoozeActionID` for identifying notification categories and snooze actions.

The `alarmURL` property specifies the location in the file system where information about the scheduled alarm is stored. The `scheduled` property is used to get and set the currently scheduled alarm. When getting it, it attempts to load alarm information from the file system and decode it. When setting it, it encodes the alarm and saves it to the file system or removes the alarm information if set to `nil`. Additionally, the custom notification `alarmUpdated` is posted to inform about updates in the scheduled alarms.

In summary, the provided code is essential for managing alarms, notifications, and notification permissions in an iOS application. The `Alarm` structure handles the scheduling and unscheduling of alarms, while the custom notification `alarmUpdated` facilitates communication regarding changes in scheduled alarms within the application. The `Codable` extension enables the saving and loading of alarm information in the file system.

#### Guided Project - Habits

##### Habits

https://github.com/Marcoc-rasi/DEVELOPMENT-WITH-SWIF-DATA-COLLECTIONS/assets/51039101/aef78543-2d64-4ab8-949c-f17b1185007f

**iOS Habit-Tracking Application - Technical Explanation**

The given code snippets are part of an iOS application for habit tracking, which functions as a social network for sharing habits. This in-depth explanation provides a detailed overview of the various components, data models, and network requests utilized within the application.

**Model Layer:**

1. **Habit Model:**
   - The `Habit` struct represents a habit and includes attributes such as its `name`, `category`, and `info`. The `category` is categorized further into a nested `Category` struct.
   - The `Habit` model conforms to the `Codable`, `Hashable`, and `Comparable` protocols, making it serializable, hashable, and comparable based on the habit's `name`.

2. **Category Model:**
   - The `Category` struct defines a category for habits, containing the `name` and `color`. The `color` is defined as a separate `Color` struct.
   - Like the `Habit` model, `Category` also conforms to the `Codable` and `Hashable` protocols, enabling serialization and making it hashable.

3. **Color Model:**
   - The `Color` struct represents a color using `hue`, `saturation`, and `brightness` values. It also conforms to the `Codable` protocol and has a computed property to convert the color into a `UIColor`.

**Network Layer:**

4. **API Requests:**
   - Several API request structs are defined, such as `HabitRequest`, `UserRequest`, `HabitStatisticsRequest`, `UserStatisticsRequest`, `HabitLeadStatisticsRequest`, `ImageRequest`, `LogHabitRequest`, and `CombinedStatisticsRequest`. Each corresponds to a specific type of API request.
   - These request structs conform to the `APIRequest` protocol. They specify the request's path, query parameters, and data (if applicable). Additionally, they handle deserialization of API responses.
   - Error handling is implemented to capture issues like missing items or failed requests.

**User Interface Layer:**

5. **HabitCollectionViewController:**
   - This view controller manages a collection view that displays a list of habits. The habits are organized into sections, including "Favorites" and categories based on the `Category` model.
   - A diffable data source, `UICollectionViewDiffableDataSource`, is used for efficient management of the collection view's data. It handles smooth updates when changes occur in the data source.
   - Each habit is presented in a cell within the collection view, and users can interact with the habits through context menus.

6. **HabitDetailViewController:**
   - This view controller displays detailed information about a selected habit. It provides a view of the habit's name, category, and related statistics.
   - Similar to `HabitCollectionViewController`, a diffable data source is used to manage and update the collection view inside this view controller.

**Diffable Data Sources:**
- The application employs diffable data sources to manage and display data in collection views efficiently. These data sources are part of the Combine framework introduced in iOS 13, allowing for smooth and efficient updates to collection views.
- Diffable data sources work with snapshots, which represent the current state of the collection view's data. They are automatically updated when changes occur.
- When new habits, categories, or sections are added, or when habits are updated, a new snapshot is created and applied to the data source. This approach is highly efficient and leads to a responsive user interface.

**Advantages of Diffable Data Sources:**
- They provide a convenient way to manage and display data within a collection view, ensuring that the UI remains synchronized with the data source.
- Diffable data sources simplify the process of inserting, deleting, or moving items within a collection view, saving developers from manually managing these operations.
- User interactions with the application result in changes to the data model that are seamlessly reflected in the UI with smooth animations, enhancing the overall user experience.

In summary, the application leverages diffable data sources to optimize the performance and user experience of collection views. These data sources automatically handle updates and animations in response to changes in the data source, making them a crucial component of modern iOS application development for the efficient management of UI components.




























