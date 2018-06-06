# CompanyStructure-USSD-PHP
Sample app created with dialog ideamart USSD PHP API's using Company Structure 

To test the app type `#780*899#` from your Dialog , Hutch numbers

# Getting Started
These instructions will get you a copy of the project up and running on your local machine or live server for development and testing purposes.

## Prerequisites
you will need to know the process of creating a connect account , Ideamart account and requesting for a hosting space
Check @pasindud [tutorial](https://www.youtube.com/watch?v=dk2C-UEKoL0)

## Installing

you can use git clone method or direct download method to download the code
```sh
	$ git clone https://github.com/djsharox/CompanyStructure-USSD-PHP.git
```
###  Make your first USSD Menu

Error log and USSD libraries are initiated in the begenning 

If we go to loadUssdSender $encoding , $chargingAmount , $version can be defined on your preference.
$password , $applicationId will be sent to the developer by the Ideamart Admins.

```sh
    $password = "XXXXXXXXXXXXXXXXXXXXXXXXXX";
    $destinationAddress = $address;
    if ($responseMessage == "000") {
        $ussdOperation = "mt-fin";
    } else {
        $ussdOperation = "mt-cont";
    }
    $chargingAmount = "X";
    $applicationId = "APP_XXXXXX";
    $encoding = "440";
    $version = "1.0";
```

MoUssdReceiver initialize the received message to a $receiver and session id stored in $receiverSessionId,finally $receiverSessionId is used to start a new session 

```sh
$receiver = new MoUssdReceiver();

$receiverSessionId = $receiver->getSessionId();
session_id($receiverSessionId);
session_start();
```
Then $receiver calls follwing methods to capture data.

```sh
$content = $receiver->getMessage(); // get the message content
$address = $receiver->getAddress(); // get the sender's address
$requestId = $receiver->getRequestID(); // get the request ID
$applicationId = $receiver->getApplicationId(); // get application ID
$encoding = $receiver->getEncoding(); // get the encoding value
$version = $receiver->getVersion(); // get the version
$sessionId = $receiver->getSessionId(); // get the session ID;
$ussdOperation = $receiver->getUssdOperation(); // get the ussd operation
```

define rhw main menu in the $responseMsg array

```sh
$responseMsg = array(
    "main" => "1.Company
                    2.Products
                    3.Careers
                    000.Exit",
    "company" => "Company Details
                    1.CEO
                    2.Location
                    3.Branches
                    4.Contact
                    999.Back",
    "products" => "Products
                    1.SDP
                    2.Soltura
                    999.Back",
    "careers" => "Careers
                    1.Software Engineer
                    2.Project Manager
                    999.Back"
);
```

use the switch statement to map the menu yoy defined in the array

```sh
  switch ($_SESSION['menu-Opt']) {
        case "main":
            switch ($receiver->getMessage()) {
                case "1":
                    $menuName = "company";
                    break;
                case "2":
                    $menuName = "products";
                    break;
                case "3":
                    $menuName = "careers";
                    break;
                default:
                    $menuName = "main";
                    break;
            }
            $_SESSION['menu-Opt'] = $menuName; //Assign session menu name
            break;
```


## Deployment
- Uploading the built Php script to hosting space

Watch Part 3 of the tutorial https://youtu.be/_6NrBCjie6o

- Provisioning (registering) your application, obtaining the app id and the password and checking in limited production

Watch Part 4 of the tutorial https://youtu.be/KhMovZXvNZQ

## License
This project is licensed under the MIT License - see the LICENSE.md file for details
