# Simple authentication API

```

<?php
header("Access-Control-Allow-Origin:*");
header("Content-Type: application/json");
header("Access-Control-Allow-Methods: POST");
header("Access-Control-Allow-Headers:Access-Control-Allow-Headers, Access-Control-Allow-Methods, Content-Type, X-Requested-with, Authorization");

//the database connection
require("connect.php");
$req = file_get_contents('php://input');
$arr = json_decode($req, true);

if (!empty($arr)) {
  
    
    $email = stripslashes(trim($arr['email']));
    $password = trim($arr['password']);
   

    $error = [];

    if (empty($email)) {
        $error[] = "email field is empty";
    }
    if (!filter_var($email, FILTER_VALIDATE_EMAIL)) {
        $error[] = "email is not a valid email";
    }
    if (empty($password)) {
        $error[] = "Password field is empty";
    }

    /**
     * if there are validation errors 
     * set the errors in a session redirect back with error
     * 
     */
    if(!empty($error)){
        http_response_code(422);
        echo json_encode(['error' => $error]);
        exit;
        }
  
        $query = "SELECT * FROM users WHERE email='$email'";
        $result = $connect->query($query);
        if($result->num_rows > 0){
            $user_details = $result->fetch_assoc();

            if($user_details['email'] == $email && $user_details['password'] == sha1($password)){
               
                echo json_encode(['user' => $user_details]);
            }
            else{
                http_response_code(400);
                echo json_encode(['error' => 'User credentials do not match our records']);
                exit;
            }
        }else{
            http_response_code(400);
            echo json_encode(['error' => 'User credentials do not match our records']);
            exit;
        }
}else{
    http_response_code(500);
    echo json_encode(["error" => "empty request"]);
}


```

connect.php

```
$connect = new  mysqli($db_host, $db_user, $db_pass, $db_name);

if($connect->connect_error){
    die("Could not connect".$connect->connect_error);
}

```