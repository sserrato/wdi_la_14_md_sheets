> [OAuth](http://en.wikipedia.org/wiki/OAuth) is an open standard to authorization. OAuth provides client applications a "secure delegated access" to server resources on behalf of a resource owner. It specifices a process for resource owners to authorize third-party access to their server resources without sharing their credentials. ~ wiki

This document covers the following topics related to OAuth:

- [An introduction to OAuth](#intro)
  * [Why use OAuth?](#why)
  * [Examples of OAuth](#examples)
  * [Other benefits of OAuth](#benefits)
  * [Alternatives to OAuth](#alternatives)
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

#### Access granularity

#### Access management

### <a name="alternatives"></a>Alternatives to OAuth

## <a name="work"></a>How does OAuth actually work?

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


## <a name="diy"></a>Do it yourself: setting up OAuth

Here, we are going to walk through the process of setting up OAuth with some common resource providers.

### <a name="github"></a>GitHub

### <a name="twitter"></a>Twitter

### <a name="instagram"></a>Instagram

### <a name="facebook"></a>Facebook

### <a name="google"></a>Google

### <a name="linkedin"></a>LinkedIn


## <a name="resources"></a>Resources for further learning
For further reading on OAuth, refer to these resources:

- [The OAuth 2.0 Authorization Framework](https://tools.ietf.org/html/draft-ietf-oauth-v2-31)
- [OAuth.net Getting Started Guide](http://oauth.net/documentation/getting-started/)
- [OAuth 2.0 & The Road To Hell](http://hueniverse.com/2012/07/26/oauth-2-0-and-the-road-to-hell/)







