# Signup with Facebook / Google using Vue

Handling SignUp or SignIn with Google and Facebook using Pure VueJS applications without any external package.

## Project setup
```
npm install
```

## Google Setup Client ID

    import GoogleAuth from '@/config/google.js'
    const gauthOption = {
    clientId: 'xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx.apps.googleusercontent.com',
        scope: 'profile email',
        prompt: 'select_account'
    }
    Vue.use(GoogleAuth, gauthOption)


 ## Options
 
 <table>
<thead>
<tr>
<th>Property</th>
<th>Type</th>
<th>Required</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>clientId</td>
<td>String</td>
<td>Required.</td>
<td>The app's client ID, found and created in the Google Developers Console.</td>
</tr>
<tr>
<td>scope</td>
<td>String</td>
<td>Optional.</td>
<td>Default value is <code>profile email</code>. <a href="https://developers.google.com/identity/protocols/googlescopes" rel="nofollow">Full list of scopes</a>.</td>
</tr>
<tr>
<td>prompt</td>
<td>String</td>
<td>Optional.</td>
<td>This value using for <a href="https://developers.google.com/api-client-library/javascript/reference/referencedocs#gapiauth2offlineaccessoptions" rel="nofollow">authCode.</a> The possible values are <code>select_account</code> or <code>consent</code>. Default value is <code>select_account</code>. To get refresh token from auth code, use <code>consent</code>.</td>
</tr>
<tr>
<td>fetch_basic_profile</td>
<td>Boolean</td>
<td>Optional.</td>
<td>If set to true, <code>email profile openid</code> will <a href="https://developers.google.com/identity/sign-in/web/sign-in" rel="nofollow">be automatically added as scope</a>. Default value is <code>true</code>.</td>
</tr>
</tbody>
</table>

## Methods
    
 <table>
<thead>
<tr>
<th>Property</th>
<th>Description</th>
<th>Type</th>
</tr>
</thead>
<tbody>
<tr>
<td>GoogleAuth</td>
<td>return of <a href="https://developers.google.com/identity/sign-in/web/reference#gapiauth2authresponse" rel="nofollow">gapi.auth2.getAuthInstance()</a></td>
<td>Object</td>
</tr>
<tr>
<td>isAuthorized</td>
<td>Whether or not you have auth</td>
<td>Boolean</td>
</tr>
<tr>
<td>isInit</td>
<td>Whether or not api init</td>
<td>Boolean</td>
</tr>
<tr>
<td>isLoaded</td>
<td>Whether or not api init. will be deprecated.</td>
<td>Function</td>
</tr>
<tr>
<td>signIn</td>
<td>function for sign-in</td>
<td>Function</td>
</tr>
<tr>
<td>getAuthCode</td>
<td>function for getting authCode</td>
<td>Function</td>
</tr>
<tr>
<td>signOut</td>
<td>function for sign-out</td>
<td>Function</td>
</tr>
</tbody>
</table>

## Usage

We already initalized GoogleAuth and directly we can add click event for the login button as below,

    loginWithGoogle () {
      this.$gAuth
      .signIn()
      .then(GoogleUser => {
        // on success do something
        console.log('GoogleUser', GoogleUser)
        console.log('getId', GoogleUser.getId())
        console.log('getBasicProfile', GoogleUser.getBasicProfile())
        console.log('getAuthResponse', GoogleUser.getAuthResponse())
      })
      .catch(error => {
        console.log('error', error)
      })
    }
    
## Facebook App ID Setup
   Important: The Facebook SDK must first be loaded asynchronously for the plugin to work. Something like this will do:

    export const initFbsdk = () => {
        return new Promise(resolve => {
            window.fbAsyncInit = function() {
                FB.init({
                    appId      : 'xxxxxxxxxxxxxxxxxxx',
                    cookie     : true,  // enable cookies to allow the server to access the session
                    xfbml      : true,  // parse social plugins on this page
                    version    : 'v2.8' // use graph api version 2.8
                });
            };
            (function(d, s, id) {
                var js, fjs = d.getElementsByTagName(s)[0];
                if (d.getElementById(id)) return;
                js = d.createElement(s); js.id = id;
                js.src = "//connect.facebook.net/en_US/sdk.js";
                fjs.parentNode.insertBefore(js, fjs);
            }(document, 'script', 'facebook-jssdk'));
        })
    }
    
   If you're not in a modular environment, just include it as a <code><script></code>.
    
    <script type="text/javascript" src="https://connect.facebook.net/en_US/sdk.js"></script>
    
### Usage
Step 1: import and use the plugin if you're in a modular environment otherwise plugin will register itself.

    import { initFbsdk } from '@/config/facebook_oAuth.js'
    
Step 2: Initialize the Facebook instance with the app id
    
    mounted () {
       initFbsdk()
    }
Step 3: Add the button click event

    loginWithFacebook () {
      window.FB.login(response => {
        console.log('fb response', response)
      }, this.params)
    }

### Compiles and hot-reloads for development
```
npm run serve
```

## [Demo Link](https://young-savannah-57214.herokuapp.com/login)
# Login Screen

<img width="565" alt="Login" src="https://user-images.githubusercontent.com/3702438/66127487-6d0a5a80-e609-11e9-86b5-034c5899765f.png">


# SignUp Screen

<img width="574" alt="SignUp" src="https://user-images.githubusercontent.com/3702438/66127630-c5d9f300-e609-11e9-991e-92a78f58140b.png">

# Facebook with SignUp/SignIn
<img width="1438" alt="Screenshot 2021-06-01 at 8 46 14 AM" src="https://user-images.githubusercontent.com/3702438/120262446-55401980-c2b7-11eb-9747-d1cdae6bea83.png">

# Google with SignUp/SignIn
<img width="1437" alt="Screenshot 2021-06-01 at 8 46 31 AM" src="https://user-images.githubusercontent.com/3702438/120262460-5a04cd80-c2b7-11eb-8da5-9f7ef20d6656.png">

### Compiles and minifies for production
```
npm run build
```

### Run your tests
```
npm run test
```

### Lints and fixes files
```
npm run lint
```

### Run your unit tests
```
npm run test:unit
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
