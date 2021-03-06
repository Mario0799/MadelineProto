---
title: setRecoveryEmail
description: Changes user recovery email. If new recovery email is specified, then error EMAIL_UNCONFIRMED is returned and email will not be changed until email confirmation. Application should call getPasswordState from time to time to check if email is already confirmed. -If new_recovery_email coincides with the current set up email succeeds immediately and aborts all other requests waiting for email confirmation
---
## Method: setRecoveryEmail  
[Back to methods index](index.md)


Changes user recovery email. If new recovery email is specified, then error EMAIL_UNCONFIRMED is returned and email will not be changed until email confirmation. Application should call getPasswordState from time to time to check if email is already confirmed. -If new_recovery_email coincides with the current set up email succeeds immediately and aborts all other requests waiting for email confirmation

### Params:

| Name     |    Type       | Required | Description |
|----------|:-------------:|:--------:|------------:|
|password|[string](../types/string.md) | Yes|Current user password|
|new\_recovery\_email|[string](../types/string.md) | Yes|New recovery email|


### Return type: [PasswordState](../types/PasswordState.md)

### Example:


```
$MadelineProto = new \danog\MadelineProto\API();
if (isset($token)) { // Login as a bot
    $this->bot_login($token);
}
if (isset($number)) { // Login as a user
    $sentCode = $MadelineProto->phone_login($number);
    echo 'Enter the code you received: ';
    $code = '';
    for ($x = 0; $x < $sentCode['type']['length']; $x++) {
        $code .= fgetc(STDIN);
    }
    $MadelineProto->complete_phone_login($code);
}

$PasswordState = $MadelineProto->setRecoveryEmail(['password' => string, 'new_recovery_email' => string, ]);
```

Or, if you're into Lua:

```
PasswordState = setRecoveryEmail({password=string, new_recovery_email=string, })
```

