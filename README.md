# GCP Credential File Comparison

This page will outline the following GCP credential files and their definitions: application_default_credentials.json, access_tokens.db, and credentials.db. Understanding how these files work and the difference between them is essential as they are often leveraged in credential compromise incidents. 

## application_default_credentials.json
The application_default_credentails.json file is a JSON file that contains credentials that can be used to authenticate to Google Cloud services. It is typically used by Google Cloud client libraries to authenticate to Google Cloud services when no other credentials are specified. 

The file can be created by running the following command: 
`gcloud auth application-default login`

This command will create a file named application_default_credentails.json in the default location for credentials on your host machine. The location of this file depends on your operating system: 
* Linux, MacOS: $HOME/.config/gcloud/application_default_credentails.json
* Windows: %APPDATA%\gcloud\application_default_credentials.json

The file contains a JSON object with the following properties:
* client_id: The client ID for the application that is using the credentials
* client_secret: The client secret for the application that is using the credentials
* access_token: The access token for the application that is using the credentials
* refresh_token: The refresh token for the application that is using the credentials

The access token and the refresh token are used to authenticate to Google Cloud services. The access token is a short-lived token that is used to make API calls. The refresh token can be used to get a new access token when the current access token expires.

The application_default_credentails.json file can be used by Google Cloud client libraries to authenticate to Google Cloud services without any additional configuration. This makes it easy to get started with Google Cloud services.

Here are some of the benefits of using the application_default_credentials.json file:
* It is easy to use. No additional configuration is required.
* It is secure. The credentials are stored in a file that is not accessible to other users.
* It is portable. The file can be moved to other machines without any problems.

## access_tokens.db and credentials.db
I will discuss the access_tokens.db and credentials.db in one section as they are both SQLite databases and are used in the same manner. 

The access_tokens.db and credentials.db files are SQLite databases that store credentials for Google Cloud services. The access_token.db file stores access tokens, which are short-lived tokens that are used to make API calls. The credentials.db file stores the refresh tokens, which can be used to get new access tokens when the current access token expires. 

The access_tokens.db and credentials.db files are typically located in the following directory:
`$HOME/.config/gcloud`

The location of these files may vary depending on your operating system. 

The access_tokens.db and credentials.db files are used by the Google Cloud SDK to authenticate to Google Cloud services. When you run a command that requires authentication, Google Cloud SDK will look for the access tokens in the access_tokens.db file. If no access tokens are found, the Google Cloud SDK will try to get a new access token by using a refresh token from the credentials.db file. 

If you are using the Google Cloud SDK, I recommend that you do not modify the access_tokens.db or credentials.db files directly. Instead, you should use the Google Cloud SDK commands to manage your credentials. For example, you can use the gcloud auth command to create, delete, and update your credentials.

## Comparison
The main difference between the application_default_credentails.json file and the access_tokens.db and credentials.db files are that the application_default_credentials.json file is a JSON file that contains the credentials, while the access_tokens.db and credentials.db files are SQLite databases that store credentials. 

The application_default_credentials.json file is typically used by the Google Cloud client libraries to authenticate to Google Cloud services when no other credentials are specified. The access_tokens.db and credentials.db files are used by the Google Cloud SDK to authenticate to Google Cloud services.

The following table summarizes the difference between the three files:
![image](https://github.com/TheIc3Root/GCP-Credential-File-Comparison/assets/7156782/23864e87-d96f-4ebc-ab94-f015e3087645)
