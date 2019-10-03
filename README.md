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
