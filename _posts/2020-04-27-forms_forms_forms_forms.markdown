---
layout: post
title:      "Forms Forms Forms Forms!"
date:       2020-04-27 15:13:39 +0000
permalink:  forms_forms_forms_forms
---


I wonder what today's topic is?!

...

It's forms.  I've found that I use forms in 90% of the projects I've worked on in the past, or am currently working on.  They're a GREAT tool that, in my opinion, can be versitile and necessary for almost every web application. For that reason, I decided it would be great to have a refreshed on forms. So here we go!

## Setting Up Our Form

Setting up the form is pretty simple. We're going to use the ```form``` tag.

```
<form className='contact-form'>

</form>
```

Above, we made out form and gave it a class name. But we aren't quite done. We're going to need somewhere to input our form data, or else pur user is just going to see a big blank screen.  So for that, we're going ti input some ```<input>``` s.


```
<form className='contact-form'>
   <input className='username-input' type='text' name='username' placeholder='Enter Your Useername...' />
	 <input className='password-input' type='text' name='password' placeholder='Enter Your Password...' />
</form>
```

Cool!  We now have a form that can take in an input for both a user's username and password!  Logging in would be just one example of form usage.  There's a wide wide world of forms out there.

## But it doesn't work...

Well of course not!  We have nothing to submit out data yet.  For that, we'll keep using out ```input``` tag.

```
<form className='signin-form'>
   <input className='username-input' type='text' name='username' placeholder='Enter Your Useername...' />
	 <input className='password-input' type='text' name='password' placeholder='Enter Your Password...' />
	 <input className='submit' type='submit' name='submit' />
</form>
```

And poof!  We have out clickable submit button in our form.  We're in business. 

## Communication is Key!

The last step is to communicate iwth the backend.  Currently, with the form as is, everything works as it should.  We can type in the input boxes, we can click the submit button.  But it doens't actually make anything happen.  From here, it's going to depend on making a request to the backend to do whatever it is our form needs to do.  

In our case of a sign-in, we would write a function to verify out user to let us sign in, or even automatically create a new user on submit. 


