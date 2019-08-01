---
layout: post
title:      "Controlled forms vs. Uncontrolled forms in React"
date:       2019-08-01 20:19:41 +0000
permalink:  controlled_forms_vs_uncontrolled_forms_in_react
---


React has two ways of handling forms: controlled and uncontrolled. But what does that mean? And when would you want to use one or the other? Let's take a look.

### Uncontrolled Forms

Uncontrolled forms are the simplest way to handle form input in React. Inputs here are handled like traditional HTML inputs, where the form data is being handled by the DOM itself, and there is no change to state. The input data only becomes available when the data is submitted, and can be accessed by a ref and a callback function. With uncontrolled form input, what you submit is what you get. 

For example: 
```
class Form extends React.Component {

     handleSubmit = (event) => {
		      const name = this.event.value
		 }

     render() {
		      return (
					     <div>
							      <input type="text" ref={input => this.event = input />
										<button onClick={this.handleSubmit}>Submit</button>
               </div>
          );
     }
```

Using uncontrolled form input is most useful when the form you are designing is very simple and has no reason to be accessable before a submit.

### Controlled Forms

When you are creating a form that is more complex, or needs to have some sort of dynamic element, controlled forms are more your cup of tea! For example, if you have a password field and you want an error to display until the required conditions of the password are met, you will need the form input to be stored and available *while* the user is typing, not simply after the user clicks submit. 

Controlled forms store the current input value as a prop, and with every change to the input field (each key stroke), a callback function is handling the change and updating the state to the current input value. Controlled forms allow the form containing component to always have access to the current input value, without having to call for it explicitly! This can be useful for in-place input validations and enforcing data input format, amongst other things. 

A controlled form might look more like this: 
```
class Form extends React.Component {
     constructor() {
		      super()
					     this.state = {
							      name: ""
							 }
		 }
		 
		 nameChange = (event) => {
		      this.setState({
					     name: event.target.value
					})
		 }
		 
		 render() {
		      return (
					     <div>
							      <form>
										     <label>Name:</label>
												 <input type="text" value={this.state.name} onChange={this.nameChange} />
												 <input type="submit" />
										</form>
							 </div>
					)
		 }
}
```

### When to use Controlled vs. Uncontrolled

Uncontrolled forms are useful when the form and input data are very basic, with minimal features. The main con to using uncontrolled forms is that there is not much extra functionality that can be attatched to your form.

Controlled forms are the way to go if you need funcitonality such as validation or instant user feedback. Writing controlled forms is more complicated, so more code will be necessary, and updating large forms may be a bit tedious.

Hopefully this helps clear up some beginner confusion about when/where/and why to use controlled vs. uncontrolled forms. 

Happy Coding!
