# Building a web page to control the robot's movement direction and linking it to a database
### This project include several basic component :

#### Web user interface
* We will use HTML CSS and JavaScript to build the interactive user interface.
* In the user interface, there will be control buttons to change the direction of the robot's movement (eg: forward, backward, right, left).
*JavaScript will be used to send robot movement control commands to the database.

ex Git :

```
<!DOCTYPE html>
<html>
<head>
    <title>Robot Control</title>
    <style>
        .button-container {
            display: flex;
            justify-content: center;
            align-items: center;
            margin-top: 20px;
        }

        .button-container button {
            margin: 0 10px;
            width: 150px;
            height: 75px;
            font-size: 20px;
            background-color: #4CAF50;
            border-radius: 5px;
        }
    </style>
</head>
<body>
    <h1>Robot Control</h1>
    <form method="post" action="control.php">
        <div class="button-container">
            <button name="direction" value="forward">Forward</button>
        </div>
        <div class="button-container">
            <button name="direction" value="left">Left</button>
            <button name="direction" value="stop">Stop</button>
            <button name="direction" value="right">Right</button>
        </div>
        <div class="button-container">
            <button name="direction" value="backward">Backward</button>
        </div>
    </form>
</body>
</html>
```




![photo1720487243 (1)](https://github.com/Rana-Ibrahim4/Web-control-page/assets/173770938/f2e9f34e-7fcc-4a34-ba08-e23ddeb1a799)





  #### Database
  * We will use a database to store information about the robot and its movement status.
  * The database will contain a table to record the commands sent from the user interface and the current status of the robot.



![photo1720487243](https://github.com/Rana-Ibrahim4/Web-control-page/assets/173770938/7df9ee9c-fa56-4141-b672-028deec34f9c)


    
  #### Connecting the user interface to the database
 * When the robot's state is updated in the database, we will use JavaScript to update the user interface immediately.
   
  ##### Linking was done using PHP code 

  ex Git :

  ```
<?php
$servername = "localhost";
$username = "root";
$password = "";
$dbname = "robot";

$conn = new mysqli($servername, $username, $password, $dbname);

if ($conn->connect_error) {
    die("Connection failed: " . $conn->connect_error);
}

if (isset($_POST['direction'])) {
    $direction = $_POST['direction'];

    $sql = "INSERT INTO direction (direction) VALUES ('$direction')";

    if ($conn->query($sql) === TRUE) {
        echo "Robot movement recorded successfully.";
    } else {
        echo "Error: " . $sql . "<br>" . $conn->error;
    }
} else {
    echo "No 'direction' value submitted in the POST request.";
}

$conn->close();
?>
```
  
 # Create a web page to display the stored data (last value)
 * What is required here is to create an HTML page that displays a specific value (the last value) of the stored data


   
   ![photo1720487243 (2)](https://github.com/Rana-Ibrahim4/Web-control-page/assets/173770938/2f34a629-2a52-4eed-a68c-40fd01beddee)

    
