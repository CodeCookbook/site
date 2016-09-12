+++
date = "2016-09-12T01:04:07-04:00"
draft = false
title = "How to Build a React Native Login Form with Redux Pt1"
videoId = "wQYDZzREBa8"
description = "Most apps require the user to login to access certain features. This video is the first in a multi-part series that will teach you how to build a login form for your react native app using redux. In this video, you'll wire up a basic component with redux."
githublink="https://github.com/CodeCookbook/LoginWithRedux/tree/part1"
+++

## Introduction

Most mobile applications require that the user login to access some kind of functionality. This video shows you how to build a react native login form with Redux. Actually, that's a lie. This is a video series and by the end of the series you'll have this login form with redux but this first video is just kind of the very basics of getting going with redux to build a login form.

Now, by the time the video series is over you'll have this login form you can type in the username and password and click this button. When you click this button, you will see this activity indicator that kind of simulates the network request and then you're brought right back here assuming the "network request" completes successfully. Also notice that i can change the orientation of the application and everything works fine. That's kind of what the finished products that looks like.

## Defining State (1:05)

Let's get started. Here's the app before anything works. You can see this button doesn't do anything. So let's let's go ahead and look at what we have here.

When we're working with redux one of the most helpful things we can do in the beginning is just think about the state that represents our application and

we're going to go ahead and define this state in the constructor so for us we have the user name of the user is typing in the field and we also have password. Now, in this case since we have that little activity indicator spinning thing, we're actually gonna need some UI state that tells us whether there is a currently pending login request so let's go ahead and add a property to our state object called "pendingLogingRequest," and this just kind of a first approximation of the state that we're going to need.

~~~javascript
class LoginWithRedux extends Component {

  constructor(props) {
    super(props);
    this.state = {
      username: '',
      password: '',
      pendingLoginRequest: false
    };
  }
}
~~~

## Defining Actions (2:12)

The next thing that's helpful to do when working with redux is to think about the actions that can actually change the state of our screen. There's several actions in our case. There's the action of the user typing in their username field. There's another action of them typing in the password field. And there's another action of actually clicking this this login button here, but we're only actually going to write down just one of these actions just that we can kind of get started with using redux here.

The action that I want to be interested in is the type username action so I'm going to create that action and then i'm going to go ahead and create the action creator for that action and we'll call that `typeUsername` and this action Creator is going to take the text that the user is typing and return an action that represents the user typing. This action is going to have a type property, which is simply the action type we've just defined. It is also going to have a text property which is the text of the users typing.

~~~javascript
const TYPE_USERNAME = 'TYPE_USERNAME';
const typeUsername = (text) => ({
  type: TYPE_USERNAME,
  text
});
~~~

## The Store (3:29)

So we have our state and we have our action. The next thing that we need is our reducer and the reducer is something that's actually passed into redux's `createStore` function so let's go ahead and grab redux. We're also going to need to grab the react bindings for redux.

Now that we have this installed we can go ahead and import the `createStore` function from redux and so let's start with that. We're gonna go ahead and create our store in this component constructor, and we're going to pass in a reducer and our initial state. The reducer takes the previous state and the action that's been dispatched and so when the user types in to this field here, what we want to do is we want to basically return new state that just incorporates the text that they've typed in here so let's do that and we're not going to worry about any other actions right now. We're just going to return a new object that spreads over state and changes the username property to the text that the user is typing.

~~~javascript
this.store = createStore((state, action) => {      
  return {...state, username: action.text}
}, this.state);
~~~

## Defining a Container Component (5:09)

Now in order to actually make sure that our redux and our actions are working properly we need to wire this up to our react application. The way that we do that is with the react redux bindings. So, we're going to need the `connect` function and we're also going to need the component called a "Provider," and I'll explain what these are in just a moment.

So this connect function returns a function that when given a react component will return a container component. Now, container components are actually intermediaries between primitive react native components and your redux store.

They do two things. One they take new state updates from the redux store and they map that state to the properties of a contained component and in this case, the contained component that we're interested in is a `TextInput`. We want this to be contained in a container component, so that it's smart about basically updates that are coming from the Redux store.

In order for this container component to act as an intermediary and we need to give it a function. Let's actually give a name for this container component. We'll call it `LoginFormTextInput` and the first parameter of the connect function is actually a function that maps from the state object that we define down here to the properties on the contained component that we want to update as a result of changes in the state.

So, this function takes a state and it returns an object that's used to set the properties on the contained `TextInput`. So what we want this to return is this value property here on this object and this value is going to be set to value prop on the `TextInput` that's contained inside of this `LoginFormTextInput` container component.

The next thing that we need this is the second parameter of the `connect` function is a
function that maps from the event props on the contained component to a function that will dispatch our actions that were interested in. In this case we're interested in the `onChangeText` event prop on the text input component.

What we want to do is we want to take the text that's being changed and we want to use that text to dispatch the type username action using this action creator that we just created a few minutes ago.

~~~javascript
const LoginFormTextInput = connect((state) => ({
  value: state.username
}), (dispatch) => ({
  onChangeText: (text) => {
    dispatch(typeUsername(text));
  }
}))(TextInput);
~~~

## Providing the Store to our Container Component (8:43)

Now, what we have is this container component that's wired up with our index store and the way that we expose this to work to this container is by using the `Provider` component that we imported from the react redux bindings.

This provider component exposes the store to all of its children and so we'll go ahead and give it the store that we've created in constructor as a prop. Next, we can actually replace this `TextInput` with a `LoginFormTextInput` and let's see what happens.

~~~javascript
<Provider store={this.store}>
  <View style={styles.container}>
  <LoginFormTextInput style={styles.textInput} placeholder="Username"/>
  <TextInput style={styles.textInput} placeholder="Password"/>
  <TouchableHighlight style={{padding: 15, backgroundColor: '#fed136'}}>
    <Text style={styles.welcome}>
      Get Cookin'
    </Text>
  </TouchableHighlight>
  </View>
</Provider>
~~~

## Testing that it works (9:40)

When I type in here let's actually make sure that the state is being updated properly. The easiest way to do that right now anyway is just to log ,it so let's go ahead and let's log our action.

So we see that we're actually getting actions dispatched to our reducer, and that these actions contain the right data.

Som there you have it you have kind of the very basics of getting started with redux in your react native application. Check back soon for the next part in this video series that you can have the entire working login form in your app.

