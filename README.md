# A Vanilla JavaScript App with Authentication

 
```bash
npm install
node .
```

### Setup Okta

Log in to your Okta Developer account (or [sign up](https://developer.okta.com/signup/) if you don’t have an account) and navigate to **Applications** > **Add Application**. Click **Single-Page App**, click **Next**, and give the app a name you’ll remember. Click **Done**.

#### Server Configuration

Open `index.js` and replace `{YOUR_OKTA_DOMAIN}` in the following code block. 

```js
const oktaJwtVerifier = new OktaJwtVerifier({
  issuer: 'https://{YOUR_OKTA_DOMAIN}/oauth2/default'
})
```

**NOTE:** The value of `{YOUR_OKTA_DOMAIN}` should be something like `dev-123456.oktapreview.com`. Make sure you don't include `-admin` in the value!

#### Client Configuration

For the client, set the `baseUrl`, `clientId`, and `authParams.issuer` in `public/main.js`.

```js
this.signIn = new OktaSignIn({
  baseUrl: 'https://{yourOktaDomain}',
  clientId: '{clientId}',
  redirectUri: 'http://localhost:8080',
  authParams: {
    issuer: 'https://{yourOktaDomain}/oauth2/default',
    pkce: false,
    responseType: ['id_token','token']
  },
  logo: '//placehold.it/200x40?text=Your+Logo',
  i18n: {
    en: {
      'primaryauth.title': 'Sign in to Calorie Tracker'
    }
  }
})
```

## Links

This example uses the following libraries provided by Okta:

* [Okta JWT Verifier](https://github.com/okta/okta-oidc-js/tree/master/packages/jwt-verifier)
* [Okta Sign-In Widget](https://github.com/okta/okta-signin-widget)

## Help

Please post any questions as comments on the [blog post](https://developer.okta.com/blog/2018/06/05/authentication-vanilla-js), or visit our [Okta Developer Forums](https://devforum.okta.com/). You can also email developers@okta.com if would like to create a support ticket.

## License

Apache 2.0, see [LICENSE](LICENSE).
