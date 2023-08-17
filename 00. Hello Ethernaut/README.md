
# Hello Ethernaut

## The final transaction
- https://mumbai.polygonscan.com/tx/0x275b5a27c14c7a97f148c3088076aeadad07d4be269dacf4bd359219ca07a5c3

## About the Contract 

- Defines a contract called `Instance` 
- Has a constructor that takes a `string` password parameter and sets it to the `password` state variable
- Implements several `info` methods that provide hints on what to call next
- `infoNum` is a hint to call `info42()` next
- `theMethodName` provides the name of the next method to call after that
- `authenticate()` takes a password and checks it against the stored `password`, setting `cleared` to true if it matches
- `cleared` is a private state variable that tracks whether the password has been validated
- To solve this contract, need to:
  - Call `info()`, `info1()`, `info2()`, `info42()` based on hints
  - Get `method7123949()` name from `theMethodName`
  - Call `method7123949()` to get password hint
  - Pass correct password to `authenticate()`
  - Call `getCleared()` to verify it worked

