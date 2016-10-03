+++
date = "2016-09-11T01:28:06-04:00"
draft = false
title = "How to Make Network Requests in React Native"
description = "Most nontrivial mobile applications need to make some kind of network request. This video shows you how to do this for a react native iOS app, even if Apple's ATS gets in your way."
videourl = "https://www.youtube.com/embed/iZpI-jqvs18?rel=0"
githublink = "https://github.com/CodeCookbook/NetworkRequestsInRN"
+++

## Introduction

Most non-trivial mobile applications require that you make some network
requests. This video shows you how to do that, and it pays particular attention to how to do that on iOS devices, which can be kind of tricky because of something called "App Transport Security." This video is brought to you by code cookbook your source for recipes for building great react native applications.

Let's go ahead and get started. So you can see here we have an iOS app, and if we scroll down to the jsx, it's rendering this view. We see that we have a touchable highlight, and what we want to do is make it so that when we click this this touchable highlight, we're going to make a network request. So let's go ahead and start doing that now, and we're going to actually get our our data from the hacker news API. So the method that's going to be invoked here when we want to make our network request is going to be called "fetch story."

So let's go ahead and bind that method in the constructor of this component.

~~~javascript
class NetworkInspector extends Component {

  constructor(props) {
    super(props);
    this._fetchStory = this._fetchStory.bind(this);
  }

  render() {
    return (
      <View style={styles.container}>
        <TouchableHighlight onPress={this._fetchStory}>
          <Text style={styles.welcome}>
            Code Cookbook
          </Text>
        </TouchableHighlight>
      </View>
    );
  }
}
~~~

## The Fetch function (1:27)

Now, react native has this global fetch function that we can use to to fetch data from the network so that's what we're going to use here and here's our URL for the hacker news api call we wanna make.

~~~javascript
class NetworkInspector extends Component {
  //...
  _fetchStory() {
    fetch('https://hacker-news.firebaseio.com/v0/item/8863.json?print=pretty');
  }
  //...
~~~

## The ATS Network Error and the Network Inspector (1:46)

So, I'm going to have to refresh this and you can see down here that there's actually an error that occurred when we tried to make our network requests, and the reason this happened is because of something called "App Transport Security." (henceforth ATS) It's a new requirement iOS 9 that requires all apps by default to use https for their network requests, and this can be problematic if we're using an API that we don't actually have control over whether that API is serving content via https or the particular certificate that's being used and all that and so what I want to show you is how you can actually tweak the app transport security settings so that you can make network requests and kind of keep developing your application.

So, let's let's go ahead and do that now, and actually before I do that I want to show you something called the network inspector so I just pressed command D on my keyboard here and this opened up the developers menu and then i can click "show inspector." There's a network tab this, and this was actually just introduced in version .33. When i click this button I can see detailed information on the particular Network requests that i tried to make.

You can see actually that the status and the timeout response we have are undefined and this is actually good evidence that your network request is failing because of ATS so let's let's go ahead and fix this now.

## Fixing Network Request Failures (3:12)

So I'm gonna go ahead and just open up the xcode project for our app. When we do we're brought to the info.plist. That's where you want to be, and there's this key here called a "transport security settings" and then there's an exception domains dictionary and we want to add a dictionary for the hacker views API so that we can kind of tweaked ATS's settings for specifically the hacker news URL or domain so let's go ahead and do that.

So, the name of the dictionary will actually be the domain name and we'll make this dictionary. You'll notice here that there's this localhost exception here and this is required because of the way that react native actually communicates with the iOS devices. Its kind of how they do hot reloading so there's this key here where they they kind of tweaked ATSs settings.

I'm not going to get into the details here, but I'm just going to copy that key so that it's underneath this dictionary that I just created here. In this particular case I actually need to add another key to tweak ATS and this key has to do with forward secrecy and I don't want that to be required in order for my network request to be successful, so I'm going to go ahead and set NO as the value there so with these two things in place i should be able to make a network request.

## Testing that our fix worked (5:35)

Now, because I've actually made this change in xcode, or, in other words, I made the change outside of JavaScript I'm actually going to need to recompile the application to make sure that these changes take effect, so let's do that now. Let's close xcode. Then I'm just going to run `run-ios` from the react native command line. It looks like that's done.

So let's go ahead and click and now we see that the network request has actually gone through, but actually here you can see that there's a 404. There's an error here, and the reason this actually happened is because we have a typo here. We're missing an "n" in the URL. Once I have that there and refresh and tap this button and then look at things in the inspector, I can see that the status code is actually two hundred and I can actually see the payload that I'm getting as a result of making the network requests.

So the network inspector is actually really handy for debugging what goes wrong with your network requests, and I definitely recommend it over logging or even putting in jsx-like text elements to kind of see what you're getting back from the network.

Well, that's it. That's how to make a basic network requests in react native. Again, this video is brought to you by code cookbook. Be sure to check back soon to see new recipes for building great react native applications.


