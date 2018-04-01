
# Mox SMS API

Mox SMS API is build for Mox SMS - Bulk SMS Application For Marketing


### Prerequisites

To run Mox SMS API you have to register to Mox SMS services. 
For more details please visit: [Mox SMS](https://www.mox.co.il/)
```
php >=5.6
Mox SMS - Bulk SMS Application For Markting
```

### Installing
Via Composer
```
composer require shamim/Mox-sms-api 
```

And Via Bash

```
git clone https://github.com/akasham67/Mox-sms-api.git
```

## Usage


 ### Step 1:
If install Mox SMS API using Git Clone then load your Mox SMS API Class file and Use namespace. 
```php
require_once 'src/Class_Mox_SMS_API.php';
use MoxSMS\MoxSMSAPI;
```
If install Mox SMS API using Composer then Require/Include autoload.php file in the index.php of your project or whatever file you need to use **Mox SMS API** classes:. 
```php
require 'vendor/autoload.php';
use MoxSMS\MoxSMSAPI;
```
### Step 2:
set your API_KEY from `https://mywebhost.com/sms-api/info` (your application install url)
```php
$api_key = 'YWRtaW46YWRtaW4ucGFzc3dvcmQ=';
```
### Step 3:
Change the from number below. It can be a valid phone number or a String
```php
$from = '8801721000000';
```

### Step 4:
the number we are sending to - Any phone number
```php
$destination = '8801810000000';
```
You have to must include Country code at beginning of the phone number.  

### Step 5:
Replace your Install URL like `https://mywebhost.com/sms/api` with `https://Moxsms.coderpixel.com/demo/`
`sms/api` is mandatory on your install url

```php
$url = 'https://Moxsms.coderpixel.com/demo/sms/api';
```
// SMS Body
```php
$sms = 'test message from Mox SMS';
```
// Unicode SMS
```php
$unicode = '0'; //For plain message
$unicode = '1'; //For Unicode message
```
// Create SMS Body for request
```php
$sms_body = array(
    'api_key' => $api_key,
    'to' => $destination,
    'from' => $from,
    'sms' => $sms,
    'unicode' => $unicode,
);
```

### Step 6: 
Instantiate a new Mox SMS API request
```php
$client = new MoxSMSAPI();
```

## Send SMS
Finally send your sms through Mox SMS API
```php
$response = $client->send_sms($sms_body, $url);
```

## Get Inbox
Get your all message
```php
$get_inbox=$client->get_inbox($api_key,$url);
```

## Get Balance
Get your account balance
```php
$get_balance=$client->check_balance($api_key,$url);
```
## Response
Mox SMS API return response with `json` format, like:

```json
{"code":"ok","message":"Successfully Send"}
```

## Status Code

| Status | Message |
| --- | --- |
| `ok` | Successfully Send |
| `100` | Bad gateway requested |
| `101` | Wrong action |
| `102` | Authentication failed |
| `103` | Invalid phone number |
| `104` | Phone coverage not active |
| `105` | Insufficient balance |
| `106` | Invalid Sender ID |


