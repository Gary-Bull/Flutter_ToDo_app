# Todo App

A minimal designed todo app, that incorporates local storage using the hive_flutter package.

## How does it work 

The folder structure inside of the /lib folder consists of 

```
/data
  database.dart
/pages
  home_page.dart
/util
  dialog_box.dart
  my_button.dart
  todo_tile.dart
main.dart
```

The `database.dart` file defines a `ToDoDatabase` class that manages the to-do list data using the Hive database. 
The `ToDoDatabase` class manages the to-do list data.
It initializes the list with default tasks if the app is opened for the first time.
It loads existing data from the Hive database.
It updates the Hive database with any changes to the to-do list.

The `main()` function inside the `main.dart` file, is an async await function, that initialises the Hive database before running the `MyApp()` widget.
The `MyApp` widget is a stateless widget that returns the MaterialApp widget, which has `HomePage()` set as home.

The `home_page.dart` file contains the HomePage stateful widget. 
Where the `_HomePageState` class initialises a Hive box for local storage and an instance of `ToDoDatabase()`, the `initState()` method is called when the widget is first created. It checks if there is existing to-do list data in the Hive box. If not, it creates initial data; otherwise, it loads the existing data.
There is a `TextEditingController` which is used to manage the text input for new tasks. 

There is also 4 other methods - 
- `checkBoxChanged()` - this method toggles the completion status of a task and updates the database.
- `saveNewTask()` - this method saves a new task to the to-do list and updates the database.
- `createNewTask()` - this method displays a custom widget called `DialogBox` to create a new task.
- `deleteTask()` - this method deletes a task from the to-do list and updates the database.

and finally the `build()` method. This method builds the UI for the HomePage widget. It includes an `AppBar`, a `FloatingActionButton` to add new tasks, and a `ListView` to display the to-do list using a custom widget called `TodoTile`.

Custom Widgets - 

- `dialog_box.dart` - this widget returns an AlertDialog box which has a text field and two custom button widgets
- `my_button.dart` - this widget returns a MaterialButton
- `todo_tile.dart` - this widget two children, a Slidable widget (which is is utilising the flutter_slidable package) and a Container which has a checkbox and text value

## Screens 

![image](https://github.com/user-attachments/assets/67faf50c-1991-44ec-a7e4-47efca06d521)
![image](https://github.com/user-attachments/assets/9eb20848-c1cf-4625-a5e2-2786e7fe5012)
