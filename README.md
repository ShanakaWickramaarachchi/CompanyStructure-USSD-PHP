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







- **Server URL** :- Send service supports only POST HTTP requests. An application wishing to initiate an MT (Mobile Terminated – Delivery of messages from an Ideamart application to a mobile subscriber’s handset) SMS message should use this.
- **Application Id** :- The developer will recieve application ID in provisioning
- **Password** :- The developer will recieve password in provisioning

Try catch method is used to capture data , **SMSReceiver** initialize the received message to a **$receiver** 
```sh
	$receiver = new SMSReceiver(file_get_contents('php://input'));
```
Then **$receiver** calls **getMessage()** , **getAddress()** and **getRequested()** to capture data.

```sh
	$content = $receiver->getMessage();
	$address = $receiver->getAddress();
	$requestId = $receiver->getRequestID();
	$applicationId = $receiver->getApplicationId();
```

 **$sender** allocate the broadcasting message to **sendMessage()** 

```sh
	$sender->sendMessage($third.",your hidden marvel character is ".$mycharacter,$address);
```

## Deployment
- Uploading the built Php script to hosting space

Watch Part 3 of the tutorial https://youtu.be/_6NrBCjie6o

- Provisioning (registering) your application, obtaining the app id and the password and checking in limited production

Watch Part 4 of the tutorial https://youtu.be/KhMovZXvNZQ

## License
This project is licensed under the MIT License - see the LICENSE.md file for details
