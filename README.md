# signup_with_facebook_google_vue

Handling SignUp with Google and Facebook using Pure VueJS applications without any external package.

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
    
## Facebook App ID Setup

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

### Compiles and hot-reloads for development
```
npm run serve
```

## [Demo Link](https://young-savannah-57214.herokuapp.com)
# Login Screen

<img width="565" alt="Login" src="https://user-images.githubusercontent.com/3702438/66127487-6d0a5a80-e609-11e9-86b5-034c5899765f.png">


# SignUp Screen

<img width="574" alt="SignUp" src="https://user-images.githubusercontent.com/3702438/66127630-c5d9f300-e609-11e9-991e-92a78f58140b.png">


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
