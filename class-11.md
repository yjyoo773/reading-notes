# Authentication

## OAuth
- Allows website and services to share assets among users.
- An open standard authorization protocol/framework that describes unrelated servers & services that can safely allow authenticated acccess to 
their assets without sharing login credentials

### Examples
- logging on websites using another website's logon service (login with Amazon, Google, Facebook, Apple, ... ....)
- sending cloud-stored files to another user via email despite the cloud storage and email system being unrelated. (Gmail & OneDrive)


### OAuth Explained
The goal for OAuth is to have two unrelated sites or softeares try to accomplish something on behalf of the user.  
Both unrelated sites/software and user have to work together involving multiple approvals for the completed transaction to be authorized.  

 OAuth is about **authorization** and not authentication in which the two have significant difference.
![Image 3-28-21 at 3 41 PM](https://user-images.githubusercontent.com/60489495/112770915-fa9bf000-8fdd-11eb-8192-551ece9cefc7.JPG)

### How OAuth Works
Assuming a user has signed into a website X. Then initiates a feature that needs to access another unrelated site/service Y.  

1. Website X connects to website Y on behalf of the user using OAuth providing user's verified identity.
2. Site Y generates a one-time token & one-time secret unique to the transaction involved.
3. Site X gives the token and secret to initiating user's client software.
4. Client's software presents the *request* token and secret to their authorization provider.
5. If not already authenticated to the authorization provider, client may be asked to authenticate afterwards. Client is asked to approve authorization transaction to website Y.
6. User approves particular transaction at website X.
7. User is given an approved access token.
8. User gives approved access token to website X.
9. Website X gives access token to website Y as proof of authentication.
10. Website Y lets website X access their site on behalf of user.
11. User sees successfully completed transaction occuring

![Screen Shot 2021-03-28 at 4 08 59 PM](https://user-images.githubusercontent.com/60489495/112771277-e9ec7980-8fdf-11eb-87da-5f416f2c3cd3.png)

source:
- https://www.csoonline.com/article/3216404/what-is-oauth-how-the-open-authorization-framework-works.html
- https://auth0.com/docs/flows
