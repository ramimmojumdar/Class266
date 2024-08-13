এই ক্লাস এর সাথে ২৬৩ নাম্বার ক্লাস যোগ আছে। 
২৬৩ নাম্বার প্রোজেক্ট দিয়ে ডাটা পাঠাই DataBage এ। আর সেই ডাটা কালেক্ট করে 266 নাম্বার প্রোজেক্ট দিয়ে।

```
<?php
header('Content-Type: application/json; charset=utf-8');

$servername = "127.0.0.1"; 
$username = "root"; 
$password = ""; 
$dbname = "my_databases"; 


$conn = new mysqli($servername, $username, $password, $dbname);

// $userInfo['name'] = "Ramim";

$sql = "SELECT * FROM user_table";
$result = mysqli_query($conn, $sql);
$rowCount = mysqli_num_rows($result);

// echo "Total row found : ". $rowCount;

$data = array();

foreach($result as $item){

    $id = $item ['id'];
    $name = $item ['name'];
    $email = $item ['email'];
    $phone = $item ['phone'];

    $userInfo ['id'] = $id;
    $userInfo ['name'] = $name;
    $userInfo ['email'] = $email;
    $userInfo ['phone'] = $phone;

    array_push($data, $userInfo);

}

echo json_encode($data);



?>
