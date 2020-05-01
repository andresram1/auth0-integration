
# Authorization

Example taken from [here](https://auth0.com/docs/quickstart/backend/python/01-authorization)

Please verify that your scope ```read:messages``` is enabled. You can do this by following these instructions:

1. In the auth0 dashboard go to `Applications`
2. Select the application you created for this exercise and click on the ```APIs``` button
3. In the Authorized API, click on the arrow ```>```
4. You'll see here which permissions are enabled.

## Install

```bash
pip install -r requirements.txt
```

## Configuration

```bash
# Set environment variables
export FLASK_APP=server.py

# THE_DOMAIN and THE_AUDIENCE must be retrieved from Auth0
export YOUR_DOMAIN=THE_DOMAIN
export YOUR_API_AUDIENCE=THE_AUDIENCE

# Similatr with THE_CLIENT_ID, THE_CLIENT_SECRET, THE_URL_TOKEN
export CLIENT_ID=THE_CLIENT_ID
export CLIENT_SECRET=THE_CLIENT_SECRET
export URL_TOKEN=THE_URL_TOKEN

```

## Run the server

In another terminal start the server. 
Don't forget to put the environment variables in this terminal
At least, the fisrt two previously mentioned

```bash
# Run the application
flask run

```

## Ask for the Token

```bash
export THE_DATA='{"client_id":"'$CLIENT_ID'", "client_secret": "'$CLIENT_SECRET'","audience":"'$YOUR_API_AUDIENCE'","grant_type":"client_credentials"}'

JWT=$(curl --request POST \
  --url $URL_TOKEN \
  --header 'content-type: application/json' \
  --data $THE_DATA | jq .access_token)

# Remove quotes...
JWT=$(echo $JWT | sed s/\"//g)

# Verify the token...
echo $JWT
```

## API Calls

```bash
curl -X GET -H "authorization: Bearer $JWT" http://127.0.0.1:5000/api/public | jq .

curl -X GET http://127.0.0.1:5000/api/public | jq .

curl -X GET -H "authorization: Bearer $JWT" http://127.0.0.1:5000/api/private | jq .

curl -X GET -H "authorization: Bearer $JWT" http://127.0.0.1:5000/api/private-scoped | jq .
```


