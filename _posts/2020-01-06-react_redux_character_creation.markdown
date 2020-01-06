---
layout: post
title:      "React/Redux Character Creation"
date:       2020-01-06 17:50:55 +0000
permalink:  react_redux_character_creation
---


So this is it, the final project.  It was definitely a challenge, but also extremely rewarding.

For this app, I recreated a Dungeons and Dragons character creation application I had previously created with Javascript and Rails.  However, this time I played around with some new features that I had excluded int he previous app, and excluded a few aspects from the previous app.

### Creating the Backend

Creating the backend for this app wasn;t to difficult given a lot of the rails generations, and minimal needs to alter those generations.

This API consisted of a User model and a Characters model.. Characters belong to a User, and a User has many Characters.  Utilizing the generations made it quick and painless to get the API up and running. 

### The Fontend (and uphill) Battle

Here's where things started to become much more difficult.  Creating my frontend proved to be quite the uphill battle, and it took a lot of trial and error, debugging, and time to even get it remotely where I was proud of my application.  Let's go over a few aspects of the app in detail.

##### Forms

First, I created my Sign In form and my Character Creation form.  These we're all to difficult to set up.  By utilizing handleChange and handleSubmit methods, creating these forms  ended up looking like this:

```
    render() {
        return (
            <div className="container">
                <h2 className="header">Begin Your Adventure Below</h2>
                <form className="sign-in-form" onSubmit={this.handleSubmit}>
                    <input className="input-username" type="text" name="username" placeholder="Enter Your Username" onChange={this.handleChange} value={this.state.username}/>
                    <input className="input-password" type="password" name="password" placeholder="Enter Your Password" onChange={this.handleChange} value={this.state.password} id="pwInput"/>
                    <input className="checkbox-toggle" type="checkbox" onClick={this.handleVisibility}/><p className="toggle-text">Show Password</p>
                    <input className="submit-user" type="submit" value="Login" />
                </form>
            </div>

        )
    }
		```
		
		With the corresponding methods:
		
		```
		    handleChange = (event) => {
        this.setState({
            [event.target.name]: event.target.value
        })
    }

    handleSubmit = (event) => {
        event.preventDefault()
        this.props.createUser({
            ...this.state,
        })
        this.setState({
            username: "",
            password: ""
        })
    }
		```
		
		The above Sign In form  also set the initial state, so that we could have multiple users saved to the backend, persisting throughout the life of the app. 
		
	#### State and Props

Understanding state and props was pivitol in getting the hand of React/Redux.  By utilizing containers that could handle state through `connect` via react-redux, it bacame easier to manage state, through the usage of `mapStateToProps`.

For example, the CharacterContainer maps through all of the created characters, passing in each character as a prop to the CharacterCard component. 

```
            <div>
                <NavBar />
                {this.props.characters.map((character) => (
                    <CharacterCard key={character.id} character={character} userId={this.props.user.id} handleDestroy={this.props.destroyCharacter}/>
                ))}
            </div>
```

This made it able to maintain stateless components that could be easily managed and easily read. 

### A Few Extra Features

Finally, I wanted to add some small quality of life features and some simple styling.

The first feature I wanted to impliment was a simple hidden password.  This was executed witht he following code: 

```    handleVisibility = () => {
        var pw = document.getElementById("pwInput")
        if (pw.type ==="password") {
            pw.type = "text"
        } else {
            pw.type = "password"
        }
    }
		
		```

Here, we used `getElementById` to hide the password input.

To style the app, I used CSSGrid to lay out my forms, inputs, headers, and other aspects of the app.

## Overall
Overall, this was a huge challenge for me.  Keeping track of state and props proved to be a lot more difficult in practice than in concept.  Using the Redux dev tools became a very quick lifesaver.  Is the project exactly where I hoped it would be? No, it still needs some work, but I'm definitely proud of where it is.  
