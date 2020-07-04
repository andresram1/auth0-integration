
---

# Disclaimer

This is an implementation heavily based on:

https://auth0.com/docs/quickstart/webapp/python/01-login


Some small modifications were considered here.


# Auth0 Configuration

- Introduce values for:
  - ```Allowed Callback URLs``` (http://localhost:3000/callback)
  - ```Allowed Logout URLs``` (http://localhost:3000)
- In the ```Advanced Settings``` section of the application:
  - Go to ```Grant Types``` and select ```Authorization Code``` option


# Configure a Google Account

- In your Google account create a Client ID (OAuth Client ID)
  - Your client appears in the ```OAuth 2.0 Client IDs``` section
  - Save the ```Client ID``` and ```Client secret``` for later use in Auth0
  - Create ```Authorized redirect URIs``` if necessary for future uses.

- In you Auth0 configuration, enable ```Social``` connections. Use the Google one
  - In the ```Applications``` section, authorize your Auth0 application to use Google.


# Configure a LinkedIn Account

Follow the instructions given [here](https://auth0.com/docs/connections/social/linkedin) and [here](https://docs.microsoft.com/en-us/linkedin/consumer/integrations/self-serve/sign-in-with-linkedin)

---

# Original Documentation

Click [here](README_ORIGINAL.md)

