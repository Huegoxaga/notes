# JavaFX

- It is a API for Java program with GUI interface
- [Click here](https://docs.oracle.com/javase/8/javafx/api/toc.htm) for official docs for JavaFX in Java ES 8.
  - It has been excluded from the offical package after SE 8, and needs to be installed from third party packages
- It follows the Observer Design Pattern by using the main thread as the Event Dispatch Thread (EDT)
  - EDT should be live all the time and has no blocking code
  - EDT is listening the user events, and it handles UI updates
  - EDT has two rules:
    - All GUI activity is on the EDT
    - No other time consuming activities can occur on the EDT
- sample starting code

```java
import javafx.application.Application;
import javafx.event.ActionEvent;
import javafx.scene.Scene;
import javafx.scene.control.Button;
import javafx.scene.control.Label;
import javafx.scene.control.TextField;
import javafx.scene.layout.Pane;
import javafx.scene.text.Font;
import javafx.stage.Stage;

public class HelloWorldGUI extends Application {

    // TODO: Instance Variables for View Components and Model
    TextField nameField;
    TextField numField;
    Label output;

    // TODO: Private Event Handlers and Helper Methods
    private void sayHandler(ActionEvent e) {
        String msg = "";
        int n = Integer.parseInt(numField.getText());
        for (int i = 0; i < n; i++) {
            msg += "Hello, " + nameField.getText() + "! ";
        }
        output.setText(msg);
    }

    /**
     * This is where you create your components and the model and add event
     * handlers.
     *
     * @param stage The main stage
     * @throws Exception
     */
    @Override
    public void start(Stage stage) throws Exception {
        Pane root = new Pane();
        Scene scene = new Scene(root, 600, 125); // set the size here
        stage.setTitle("Hello"); // set the window title here
        stage.setScene(scene);
        // TODO: Add your GUI-building code here

        // 1. Create the model
        // 2. Create the GUI components
        nameField = new TextField("World");
        numField = new TextField("1");
        Button sayButton = new Button("Say It!");
        output = new Label("---");

        // 3. Add components to the root
        root.getChildren().addAll(nameField, numField, sayButton, output);

        // 4. Configure the components (colors, fonts, size, location)
        nameField.relocate(0,35);
        numField.relocate(0,65);
        sayButton.relocate(0,95);
        output.setPrefWidth(600);
        output.setFont(new Font("System", 20));
        output.setStyle("-fx-background-color: lightblue;-fx-text-fill:darkblue;");

         // 5. Add Listeners and do final setup(draw the first view after loaded)
        sayButton.setOnAction(this::sayHandler);

        // 6. Show the stage
        stage.show();
    }

    /**
     * Make no changes here.
     *
     * @param args unused
     */
    public static void main(String[] args) {
        launch(args);
    }
}
```

- RequestFocus is used to auto-select the text after execution
- setGraphic adds image
- getSource will get the action content
- a::b reference object a to method b
- Thread handler can hijack the program
- Threads can hijack the event handlers.

## Colorpicker object

### Create new object

```java
final ColorPicker colorPicker = new ColorPicker(Color.default);
```

### Methods

```java
Color c = colorPicker.getValue();
.getRed()
.getGreen()
.getBlue()
```

## Style

- simple Button, MenuButton(default) and SplieMenuButton

```java
colorPicker.getStyleClass().add("button");
//or
colorPicker.getStyleClass().add("split-button");
```

## Cursor

- `scene.setCursor(Cursor.type);`
- `scene.getCursor();`

## Button

- `.setOnAction()`
- `.setOnMouseEntered()`
- `.setOnMouseExited()`
- `.setDisable(boolean)` make it not clickable

### Mouse Events

- add a mouse event handler

```java
canvasName.addEventHandler(MouseEvent.MOUSE_PRESSED, this::newHandlerName);
//or
canvasName.setOnMouse(Entered/Exited etc)(this::Handler);
```

- Events

  - `MouseEvent.MOUSE_PRESSED`
  - `MouseEvent.MOUSE_RELEASED`
  - `MouseEvent.MOUSE_MOVED`
  - `MouseEvent.MOUSE_DRAGGED` //for drag any movement is one event.
  - `MouseEvent.MOUSE_ENTERED`
  - `MouseEvent.MOUSE_EXITED`

- add event handler method:

```java
private void newHandlerName(MouseEvent x) {
}
```

- get MouseEvent object info

```java
x.getX(); //X location of the mouse
x.getY(); //Y location
x.getButton(); //return String? which button is clicked
```

### Radio Button

```java
ToggleGroup group = new ToggleGroup();
//This enables only one button can be selected at the same time.
    RadioButton button1 = new RadioButton("select first");
    button1.setToggleGroup(group);
    button1.setSelected(true);
    RadioButton button2 = new RadioButton("select second");
    button2.setToggleGroup(group);

if(button1.isSelected()==true){
//etc
}
```

### Alert windows

`new Alert(Alert.AlertType.WARNING, “Alert message").showAndWait();`

### Stage

- `primaryStage.setMinHeight(200);`
- `primaryStage.setMinWidth(200);`

### Font

- `.setFont(new Font("System", 20));`

### Color

### Style

`hint.setStyle("-fx-background-color: lightblue;-fx-text-fill:darkblue;”);`

### ChioceBox

- It is a drop down menu.

#### New Choice Box

`ChioceBox chioceBox = new ChoiceBox();`

#### Add options

`cb.getItems().addAll("option1", "option2", "option3");`

#### Get selected value

`String selected = (String)chioceBoxName.getValue();`

#### Set the Default for Selected Item

```java
chioceBoxName.getSelectionModel().selectFirst();
//or
chioceBoxName.getSelectionModel().select(int index);
```

### Tooltip

- it is a small floating label provide hints when mouse over any GUI object

`GUIobject.setTooltip(new Tooltip(“Select the language”));)`

### setLineWidth

```java
double canvasHeight = g.getCanvas().getHeight();
setPrefWidth();
setStyle()  ->
"-fx-border-color: blue;\n" +
"-fx-border-insets: 5;\n"  +
"-fx-border-width: 3;\n" +
"-fx-border-style: dashed;\n";
```

## JavaFX Concurrent Package

- It contains the classes required to allow background threads to run complex calculations

### Task

- It defines a background task for an UI

```java
public class BackgroundTask extends Task<String> {
    @Override
    public String call() {
        pause(1000);  // waits 1 second tp simulate a large task
        updateValue("123"); // Call the observable property to update the JavaFX UI's binded property
        return Integer.toString(i);
    }
}
```

### Service

- It is designed to execute the Task object
- It knows about the EDT (Event Dispatch Thread)
- It is designed to help with managing multithreaded code
- Service must be initialized and accessed from the EDT (main)

```java
public class BackgroundService extends Service {
    public Task createTask(){
        return new BackgroundTask(); //Init a Task class for a Service
    }
}
```

#### Service Methods

- In the event handler from the EDT, a service can be executed using the following methods
- `label.textProperty().bind(service.valueProperty());` bind the service to a property of an UI
  - A JavaFX component can bind its `valueProperty()` or `messageProperty()` to a service
- `service.start();` start the task, the task must be in the READY state
- `service.cancel();` cancel the task
- `service.restart();` restart the task
- `service.reset();` reset the task, the service must be in one of the finished states (SUCCEEDED, FAILED, CANCELLED OR READY)
- `label.textProperty().unbind();` unbind the task, must unbind the property if it was bound, before updating the property's value in the EDT manually

Documentation
Rules.

Platform
Platform.runLater  
This makes all graphical method run in a queue when making fast animate. This is a good practice for the program to make it smooth.
