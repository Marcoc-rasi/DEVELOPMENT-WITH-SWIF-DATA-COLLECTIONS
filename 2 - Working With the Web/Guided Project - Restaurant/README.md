# `Guided Project: Restaurant`

In this unit, I acquired new tools in Swift and learned how to send and retrieve information through a web services API. In the guided project, I put my knowledge to the test by designing an interactive menu for a restaurant that allows the customer to view a list of options, add items to an order, and submit the order to the restaurant. Using a server running on my own computer, I had the opportunity to modify the options, descriptions, and images returned by the API.

## `Server Details and Project Setup`
Before delving into the workflow of the menu application, it's crucial to understand how to work with the server. By comprehending the API and server functionality, I could outline a set of features for the project. While no modifications were necessary for the server data, running the server on my Mac was essential.

## `Running the Server`
The project folder includes the server's binary file, OpenRestaurant.app. I right-clicked on OpenRestaurant and selected "Open" from the dropdown menu. Depending on my Mac's security settings, a warning dialog might appear. I clicked "Open" to indicate my trust in the application.

![SERVER_1](https://github.com/Marcoc-rasi/DEVELOPMENT-WITH-SWIF-DATA-COLLECTIONS/assets/51039101/5c1f546d-c115-4c95-9c20-384e8f463c03)


To start and stop the server, I clicked the button in the bottom-right corner of the OpenRestaurant window. If I made changes to the server's resource files, I needed to stop and restart the server.

![SERVER_2](https://github.com/Marcoc-rasi/DEVELOPMENT-WITH-SWIF-DATA-COLLECTIONS/assets/51039101/8b38f700-1f62-471e-9b16-dbf57790d68a)


The server allowed me to view menu categories and items, edit categories and items, and open the image folder. Clicking "Edit Categories" or "Edit Menu Items" opened categories.json or menu.json, respectively. These files contained the data returned by the server. If I wanted to change the menu, I needed to edit one or both files.
Clicking "Open Image Folder" provided access to a directory containing fictional images for menu items. If I wanted to add my own food images to this directory, I made sure to use PNG images. Each menu item's image was named after its ID.

I started the server with the button in the bottom-right corner. To verify the server's correct operation, I opened my browser and loaded the URL http://localhost:8080. The browser should display text on the screen indicating the server's status. If I encountered an error, the most common cause was incorrect editing of menu.json, preventing the menu list from being created correctly. I needed to ensure that the JSON data was valid, close the application window, and restart the server. I could use the "Reset Data" button to discard my custom data and restore the original files.

Depending on my Mac's settings, I might see a request to allow incoming connections to the server. I clicked "Allow."

![SERVER_3](https://github.com/Marcoc-rasi/DEVELOPMENT-WITH-SWIF-DATA-COLLECTIONS/assets/51039101/6783db5b-4e9e-4e97-989c-458625c8a58d)


## `JSON Structure`
I opened menu.json from the OpenRestaurant window, then opened http://localhost:8080/menu in my browser to view the menu data the API would return. At the root level of the JSON, there is an array of dictionaries, where each dictionary represents a menu item. If I closely examined the server data compared to menu.json, I noticed that the JSON didn't exactly match. I wasn't concerned about the discrepancy; the server makes some adjustments to the data structure when it receives a request.
In each dictionary of the JSON returned by the server, I found the following keys:
- `id` is a unique Int that distinguishes one item from another. If I added or modified a dictionary, I ensured that each `id` value was unique.
- `name` is a String indicating the name of the menu item. The server doesn't require names to be unique, but it wouldn't make sense to have two items with the same name on a menu, so I kept names unique.
- `description` is a String providing more details about the menu item.
- `price` is a Double expressing the menu item's price. In the sample data, values are in US dollars. However, price values aren't tied to a specific currency, so I could adjust them to any currency I desired.
- `category` is a String providing a way to divide items, as in a real menu. In the sample data, categories are "appetizers," "salads," "soups," "main courses," "desserts," and "sandwiches." If I wanted to create a new menu item, I assigned the corresponding category key. If I wanted to create a new category, such as "side dishes," I added it to category.json.
- `image_url` is automatically created by the server and has the server's base URL followed by the image path and then the image's name. The image's name is also automatically created by the server and is the item's id followed by the .png file extension. If I wanted to add my own image, I made sure the name corresponded to the item's id and that its extension was also .png.

When modifying menu.json, I only needed to use the keys `id`, `name`, `description`, `price`, `category`, and `estimated_prep_time`. The last key doesn't appear in the JSON returned by the server for menu items, but the server uses it to provide an estimate of how long it will take to fulfill an order. The server is configured to use these keys (and only these keys). If I added other keys to a dictionary, the server would ignore them.

## `Server Endpoints`
The API in this project has several URLs to implement the application's functions. Each URL starts with http://localhost:8080 and can be combined with the following endpoints:
- `/categories`: A GET request to this endpoint will return an array of strings representing the categories in menu.json. The array will be available under the key `categories` in the JSON.
- `/menu`: A GET request to this endpoint will return the complete array of menu items. It can also be combined with the query parameter `category` to return a subset of items. The array will be available under the key `items` in the JSON.

- `/images`: Combined with the image name, a GET request to this endpoint will return the data of the image associated with a menu item.

- `/order`: A POST to this endpoint with a collection of menu item ID values will send the order and return a response with the estimated time before the order is ready. The IDs you send must be contained in JSON data under the key `menuIds`. When parsing the JSON, the estimated preparation time before the order is ready will be under the key `preparation_time`.


### `OrderApp`

https://github.com/Marcoc-rasi/DEVELOPMENT-WITH-SWIF-DATA-COLLECTIONS/assets/51039101/dfd7603b-7a66-4335-83dc-32214a9fde82

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


## `State Restoration`

Consider the following scenario: A user starts an order by adding one or two items to the menu. Then, they get interrupted by an iMessage notification, resulting in 15 minutes of text messages, emails, and web browsing. When the user returns to your application, it has closed. Instead of picking up where they left off, they have to create the order from scratch, which is not a good experience. Furthermore, their menu exploration state has reset to the list of categories, another inconvenience if the menu hierarchy is deep and there are many items. (You probably noticed these shortcomings while developing the application.)

By implementing state restoration, you can ensure that the user perceives no interruption in their activity. This is also crucial for iPad applications that support multiple windows to provide a good user experience.

Starting from iOS 13, state restoration is handled by your UIWindowSceneDelegate and is achieved through the NSUserActivity class. NSUserActivity is a lightweight object that enables various functions on Apple platforms, including state restoration, Handoff, Spotlight search indexing, and SiriKit. You can instantiate NSUserActivity at key moments and provide the necessary contextual information to perform these tasks.

In this extension of the guided project, you will add state restoration to OrderApp. For this application, you will maintain an instance of NSUserActivity in MenuController containing the current order, as well as the necessary elements to recreate the view controllers in your application where the user might have stopped working.

Here's how it works: While the user is using your application, you will track key information in the userInfo dictionary of an instance of NSUserActivity. When your scene goes into the background, iOS will request an instance of NSUserActivity that will be used the next time the scene connects. When the scene reconnects, you will be provided with the same instance of NSUserActivity, which you can use to reconstruct the application state so that the user can continue with what they were doing.

## `summary`
I acquired fundamental knowledge about key concepts in modern applications. I explored complex topics in this unit. Firstly, I understood closures and their function in passing code between objects, creating executable blocks later on. Subsequently, I applied closures to develop animations. Lastly, I learned how to make network requests to fetch information from the web and send data back.

With the ability to work with public APIs, my applications are no longer limited to the information users input. I now have access to the entire worldwide web. In the next unit, I delved into collection views, essential tools in iOS that allow displaying extensive collections of information with an almost infinite variety. I reinforced my existing skills and discovered common patterns that will make future exploration in UIKit more familiar.
