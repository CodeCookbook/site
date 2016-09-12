+++
date = "2016-09-09T18:58:27-04:00"
draft = false
title = "How to Share Text from your React Native App"
description = "Sometimes you want your react native app to be able to share its own data with external applications like the email app or the Facebook app. This 8 minute recipe shows you how to do this."
githublink =  "https://github.com/CodeCookbook/ShareText"
videoid = "ACryo-rCrQk"
+++

## Introduction

Sometimes when you're building a mobile application you want to be able to share data from the application to an external application like an email app or maybe Facebook Twitter.

This recipe shows you how to do this this recipe is from code cookbook your source for short video recipes on how to build great react native applications. Let's go ahead and get started.

So, you can see here that we have a simple react native application. This is actually generated from the `init` command from the reactive command-line interface, and all were doing here right now is showing this code cookbook text so let's actually change this to a more appropriate text so we want to share.

## Simple Sharing (1:00)

Now, when we click this button, we actually want to be able to share something to the mail application, and so let's go ahead and import `Share` from react-native. We're going to go ahead and add a method that will be called that will actually work with this share here from the reactive module so let's let's go ahead and do that now so we have this share message and we actually need to go ahead and define this in our component let's do that. Now, we can go ahead and define method now so we have this share message method and like we said we want to actually do share some data when we invoke this method and so the API for for the share module is just this share method and then we can pass it an object with a message property that holds the information that we want to share.

So, we can say "This is a simple shared message." The share method actually returns promise, so we're going to go ahead and pass a method that will handle the result of the promise and we'll call this "showResult," so we need to go ahead and create a method for that and this method will go ahead and set some state which we'll "result"

We need to go ahead and initialize this state here in the constructor. And now we should have a really simple working share example. Let's go ahead and add a simple text component here that will display a result of calling share. We're going to go ahead and do just going to stringify the result.

Let's go ahead and refresh this, and you see if we can get something working so i'm gonna go ahead and cancel here just to make sure that everything's working, and you can see that the result promise created this action and it just tells us that we've kind of dismissed that the share action sheet that we didn't actually do anything. However, if we click this again and we go to the mail application is up you'll see that the mail the email here is populated with the content from this message property, so we know that that's working properly and we can actually go ahead and send this.

When it's actually sent you can see that that the object that gets kind of resolved by the promises little different it has the action of shared action here and then it tells us the type of the activity that actually that we actually shared the message to. So, this is how we do kind of really simple sharing of data to external applications.

~~~javascript
class ShareLesson extends Component {

  constructor(props) {
    super(props);
    this._shareMessage = this._shareMessage.bind(this);
    this._showResult = this._showResult.bind(this);
    this.state = { result: ''};
  }

  _showResult(result) {
    this.setState({result});
  }

  _shareMessage() {
    Share.share({
      message: 'This is a simple shared message'
    }).then(this._showResult);
  }

  render() {
      return (
        <View style={styles.container}>
          <TouchableHighlight onPress={this._shareMessage}>
                  <Text style={styles.welcome}>
                    Share
                  </Text>
          </TouchableHighlight>
          <Text>
            {JSON.stringify(this.state.result)}
          </Text>
        <View>);
  }
}
~~~

## Fancy Sharing (5:05)

However, you can actually get a little bit more fancy when we do this and so let's let's go ahead and show what that looks like. There are more options that we have when we're sharing sharing data to other applications, and so let's let's explore those. So now we have this fancy share and we're going to have a separate method. This one's gonna be called "fancyShareMessage," and we're gonna have to go up here.

So, now this time when we call share we're actually going to pass in we're actually going to pass in not only a message but also a URL. Again, this is a promise so we need to pass in a function that will be called when the promise gets resolved. Let's go to refresh this and we open up the mail application this time, you'll notice that there's a message and a URL that populates the email. So, that's that's one way that we can get a little bit fancy here with our with our share.

Now, if you look at the example in the UI explore react native there's actually a title property that they they use in the example, but in my experience that doesn't really seem to do anything it might just be that i'm not opening the right application to share data to.

However, there is another parameter that this takes and these are options that customize the look of the dialogue action sheet that appears when you try and share something so. For example, I can specify a tint color property. When I refresh this and click fancy share you'll notice that this cancel button here is green, so I said that the tint color here and I've kind of customize the appearance of this.

Now again there's another property that's set here in the in the example application from the Explorer UI and that property is dialogue title, and again this doesn't seem to matter much, so i don't really worry about it.

~~~javascript
_fancyShareMessage() {
  Share.share({
    // title: ''
    message: 'This is a fancy shared message',
    url: 'http://codecookbook.co'
  }, {
    tintColor: 'green',
    // dialogTitle: 'This doesnt matter much'
  }).then(this._showResult);
}
~~~

## Conclusion (8:02)

So now you've just seen how you can share data external to react native application. You've seen kind of a basic share case and a share case that has a little bit more options.

Well that's it i hope you enjoyed this recipe from the cookbook be sure to check back soon for a new recipe.
