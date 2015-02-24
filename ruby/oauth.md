# What is OAuth?

> [OAuth](http://en.wikipedia.org/wiki/OAuth) is an open standard to authorization. OAuth provides client applications a "secure delegated access" to server resources on behalf of a resource owner. It specifices a process for resource owners to authorize third-party access to their server resources without sharing their credentials. ~ wiki

This document covers the following topics related to OAuth:

## Table of contents

- [An introduction to OAuth](#intro)
  * [Why use OAuth?](#why)
  * [Examples of OAuth](#examples)
  * [Other benefits of OAuth](#benefits)
- [How does OAuth actually work?](#work)
  * [Resource providers that use OAuth](#providers)
- [A brief history of OAuth](#history)
  * [OAuth 1.0 vs 2.0](#vs)
- [Do it yourself: setting up OAuth](#diy)
  * [Github](#github)
  * [Twitter](#twitter)
  * [Instagram](#instagram)
  * [Facebook](#facebook)
  * [Google](#google)
  * [LinkedIn](#linkedin)
- [Resources for further learning](#resources)

## <a name="intro"></a>An introduction to OAuth

Essentially, OAuth allows a **resource provider** (like Facebook or Github) to give a **resource owner** (aka you) permission to give their **third-party** (for example, your application) access to the resource providers information. You can think of OAuth as a 3-way triangle of authentication.

### <a name="why"></a>Why use OAuth?

OAuth, as an authorization framework, tries to solve security challenges related to authentication such as:

1. API provider (aka resource provider) has to authenticate both the end user and the developer.
2. The end user needs to be able to both grant and revoke permissions.
3. The API provider wants to give different permissions to different developers based on level of trust.
4. The end user wants to give the developer access to the resource provider on his/her behalf.

### <a name="examples"></a>Examples of OAuth


Here are some examples of OAuth in action:

- A game  posts to Facebook on behalf of its users (the game players).
- An app requires sign in via the users' Twitter profiles.
- A community allows you to find more friends based on your LinkedIn connections.

### <a name="benefits"></a>Other benefits of OAuth

#### Varying access levels
You can give different permissions to different users, like read-only vs. read-write.

#### Access granularity
You have the freedom to decide how much data you grant access to. For example, you might grant access to your friend list only, or just to your profile information.

#### Access management
You are able to manage third-party access directly from the resource provider. For example, you can cancel third-party application access to yoru Facebook profile directly from your Facebook account settings. You do not have to go to the third-party application to cancel and revoke access.

## <a name="work"></a>How does OAuth actually work?

Good question. In a nutshell, OAuth allows you to give permission for one application to interact with another, without giving away your password.

Below, in non-technical terms, is an variation of the OAuth love triangle, as deemed by [Rob Sobers](http://blog.varonis.com/introduction-to-oauth/).

#### Step 1: Showing intent
Here, the user says: "Hi Buffer App, I want you to post my scheduled social media posts to my Facebook page on my behalf."

Then, the third-party app says "Coo. Let me go ask Facebook for permission."

#### Step 2: Receiving permission
Next, the third-party app asks the resource provider (in this case, Facebook): "One of your users would like me to post to his page. Can I get a request token from you?"

The resource provider, Facebook replies: "Of course. Here's a token and secret. Guard them with your life so no request forgery occurs."

#### Step 3: User redirected to resource provider
Next, the third party app, Buffer, sends the user over to the resource provider, Facebook, for approval. The user must take the request token with them.

#### Step 4: User gives permission
The user then arrives to Facebook, telling it: "I want to authorize this request token from Buffer App".

Facebook confirms: "Ok, are you sure you want Bufer to be able to post on your page on your behalf?"

The user, confirms, hopefully.

#### Step 5: 3rd-party gets access token
At this point, the user is redirected back to the third party app, in this case, Buffer.

Buffer then asks the resource provider, Facebook, to exchange their request token for an access token.

Facebook then provides Buffer with an access token and secret.

#### Step 6: 3rd-party access protected resource
Finally! Buffer now has succifient tokens to access Facebook's posting permissions on the user's behalf.

Phew, that was long.

#### In summary...
The user never had to share Facebook login credentials with Buffer. Rather, he just delegated access using OAuth.

Should the user wish to revoke access, he/she can do so by logging into Facebook and revoking the tokens for Buffer.


### <a name="providers"></a>Resource providers that use OAuth

Here are some of the most popular resource providers that use OAuth, as well as links to related documentation:

- [Amazon](http://login.amazon.com/)
- [Basecamp](https://github.com/basecamp/api/blob/master/sections/authentication.md)
- [Dropbox](https://blogs.dropbox.com/developers/2013/07/using-oauth-2-0-with-the-core-api/)
- [Etsy](https://www.etsy.com/developers/documentation/getting_started/oauth)
- [Evernote](https://dev.evernote.com/doc/articles/authentication.php)
- [Facebook](https://developers.facebook.com/docs/reference/dialogs/oauth)
- [Flickr](https://www.flickr.com/services/api/auth.oauth.html)
- [Foursquare](https://developer.foursquare.com/overview/auth)
- [GitHub](https://developer.github.com/v3/oauth/)
- [Google](https://developers.google.com/accounts/docs/OAuth2)
- [Instagram](http://instagram.com/developer/authentication/)
- [LinkedIn](https://developer.linkedin.com/docs/oauth2)
- [Mailchimp](https://apidocs.mailchimp.com/oauth2/)
- [OAuth](https://github.com/reddit/reddit/wiki/OAuth2)
- [Paypal](https://developer.paypal.com/docs/integration/direct/paypal-oauth2/)
- [Soundcloud](https://developers.soundcloud.com/docs)
- [Stripe](https://stripe.com/docs/connect/oauth)
- [Trello](https://trello.com/docs/gettingstarted/oauth.html)
- [Twitter](https://dev.twitter.com/oauth)
- [Yelp](http://www.yelp.com/developers/documentation/v2/authentication)


## <a name="history"></a>A brief history of OAuth

### <a name="vs"></a>OAuth 1.0 vs 2.0
OAuth 2.0 recently (although not in web terms -- October 2012) replaced OAuth 1.0. It focused on developer simplicity. There are competing opinions about the direction of 2.0, but here is a simplified explanation about the "improvements":

#### Separation of Roles

OAuth 2.0 provides a clear spearation of roles between the authorizatoin server authenticating and authorizing the client and that of the resource server handling API calls.

#### Address Native Applications
OAuth 1.0's flow did not manage that of native applications for mobile well. In 2.0, flows are are specifically defined for native applications.

#### Request Signing
Prior, signatures had to be generated and validated on the server for every API requiest received. Now, this process is simpler as all tokens are sent over SSL.
 

## <a name="diy"></a>Do it yourself: setting up OAuth

Here, we are going to walk through the process of setting up OAuth with some common resource providers.

Consider using [Lorin's demo app](https://github.com/lorint/OAuthSamples2) to assist you with this.

### <a name="github"></a>GitHub
1. Go to GitHub profile.
2. Register new application: [https://github.com/settings/applications
](https://github.com/settings/applications)
3. Make sure the authorization callback URL is: http://localhost:3000/github
4. Set the client ID and client secret by running the following command line:

```
$ atom ~/.bash_profile
export GH_CLIENT_ID=[youridhere]
export GH_CLIENT_SECRET=[yoursecrethere]
```

5. Close out all instances of Terminal (or your command line interface).
6. Check in Terminal that everything was saved by typing in the following:

```
$ echo $GH_CLIENT_ID
$ echo $GH_CLIENT_SECRET
```

### <a name="twitter"></a>Twitter



### <a name="instagram"></a>Instagram

1. Go to Instagram developer docs: [http://instagram.com/developer/](http://instagram.com/developer/)
2. Register your account.
3. Register client.
4. Ensure that the OAuth-redirect-url is something like: http://localhost:3000/instagram
3. Review the Instagram docs for authentication: [http://instagram.com/developer/authentication/](http://instagram.com/developer/authentication/)
4. Set the client ID and client secret, the same way you did prior.

```
$ atom ~/.bash_profile
export IG_CLIENT_ID=[youridhere]
export IG_CLIENT_SECRET=[yoursecrethere]
```

5. Close out all instances of Terminal (or your command line interface).
6. Check in Terminal that everything was saved by typing in the following:

```
$ echo $IG_CLIENT_ID
$ echo $IG_CLIENT_SECRET
```

### <a name="facebook"></a>Facebook

### <a name="google"></a>Google

### <a name="linkedin"></a>LinkedIn


## <a name="resources"></a>Resources for further learning
For further reading on OAuth, refer to these resources:

- [The OAuth 2.0 Authorization Framework](https://tools.ietf.org/html/draft-ietf-oauth-v2-31)
- [OAuth.net Getting Started Guide](http://oauth.net/documentation/getting-started/)
- [OAuth 2.0 & The Road To Hell](http://hueniverse.com/2012/07/26/oauth-2-0-and-the-road-to-hell/)
- [OAuth 2.0: Benefits & Use Cases - Why?](http://stackoverflow.com/questions/7561631/oauth-2-0-benefits-and-use-cases-why)
- [OAuth: Pros & Cons of OAuth](http://www.socialtechnologyreview.com/articles/oauth-pros-and-cons-oauth)







