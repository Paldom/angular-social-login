# Angular Social Login (ngSocialLogin)
Angular Social Login module (for PhoneGap/Cordova)

Supported sites:
- Google
- Facebook

## Requirements

Complete functionality only available in __PhoneGap/Cordova__ applications with __inAppBrowser__ plugin (https://github.com/apache/cordova-plugin-inappbrowser) installed.

## Installation

### via npm

```shell
npm install angular-social-login
```

### via bower

```shell
bower install angular-social-login
```

### configure installation

Include JS file:

```html
<script src="/bower_components/angular-social-login/angular-social-login.js"></script>
```

Then include `ngSocialLogin` as a dependency for your app:

```javascript
angular.module('myApp', ['ngSocialLogin']);
```

## Configuration

### Example

```javascript
app.config(['$googleDefaultsProvider', '$facebookDefaultsProvider',
    function ($googleDefaultsProvider, $facebookDefaultsProvider) {

        $googleDefaultsProvider.useConfig({
            client_id: 'YOUR CLIENT ID',
            client_secret: 'YOUR CLIENT SECRET',
            scope: 'YOUR SCOPES, E.G.: https://www.googleapis.com/auth/userinfo.email'
        });

        $facebookDefaultsProvider.useConfig({
            client_id: 'YOUR APP ID',
            scope: 'YOUR SCOPES, E.G.: email,read_stream,publish_actions'
        });

}]);
```

## Usage

### Methods

- `$googleDefaultsProvider.useConfig(config)`
- `$facebookDefaultsProvider.useConfig(config)`
- `$googleAuth.getAuthURL(authConfig)`
- `$googleAuth.getAccessToken(authCode, customConfig, customURL)`
- `$facebookAuth.getAuthURL(authConfig)`
- `$socialAuthCordova.loginGoogle(authConfig, customConfig, customURL)`
- `$socialAuthCordova.loginFacebook(authConfig, customConfig, customURL)`
- `$socialAuthCordov.login(site, authConfig, customConfig, customURL) `

### Params
- __config/authConfig__: 
```javascript
{
    client_id: YOUR CLIENT ID,
    redirect_uri: REDIRECT URI,
    response_type: RESPONSE TYPE,
    scope: SCOPE
}
```
- __customConfig__: override authConfig for accessToken request (e.g. client_secret, grant_type)
- __customURL__: custom URL to call access token requests (e.g. server proxy)

### Example

```javascript
$socialAuthCordova.loginGoogle(authConfig, customConfig, customURL).then(function (res) {
    console.log(res.access_token);
}, function (error) {
    console.log(error);
});

$socialAuthCordova.loginFacebook(authConfig, customConfig, customURL).then(function (access_token) {
    console.log(access_token);
}, function (error) {
    console.log(error);
});
```