---
title: "Controllers and validation with Waffle"
description: ""
date: "2008-11-20T00:00:00.000Z"
categories: []
published: true
canonical_link: https://javame.netlify.app//controllers-and-validation-with-waffle-43c667a47d11
redirect_from:
  - /controllers-and-validation-with-waffle-43c667a47d11
---

One of the nicest features of [Waffle](http://waffle.codehaus.org/) are the [Validators](http://waffle.codehaus.org/validation.html).   
In order to have server side validation on some controller logic you don’t need to extend or write any fluff.   
Given a method on your controller like this one:

```
package waffle.controllers;

import org.codehaus.waffle.view.RedirectView;
import org.codehaus.waffle.view.View;

public class UserLoginController {

public View login(String username, String password) {
            return new RedirectView(&quot;homepage.waffle&quot;);
    }

}
```

All you have to do is write a class named UserLoginControllerValidator (just for convention, not strictly necessary) and a method with the same syntax as the action on the Controller with also the ErrorsContext parameter in the signature.

For a simple application login it will look more or less like this:

```
package waffle.validators;

import org.codehaus.waffle.validation.ErrorsContext;
import org.codehaus.waffle.validation.FieldErrorMessage;

import waffle.services.AuthenticationExeption;
import waffle.services.AuthenticationService;

public class UserLoginControllerValidator {

private final AuthenticationService authenticationService;

public UserLoginControllerValidator(AuthenticationService authenticationService) {
                this.authenticationService = authenticationService;
        }

public void login(ErrorsContext errors, String username, String password) {
                try {
                        authenticationService.login(username, password);
                } catch (AuthenticationExeption exeption) {
                        errors.addErrorMessage(new FieldErrorMessage("name", username, exeption.getMessage()));
                }
        }
}
```

Well the design is pretty clean right?   
There’s no coupling, there is no inheritance involved and the responsibilities of the classes are well isolated: the controller controls, redirects, the validator validates.

With such an easy design also testing becomes easier.   
Here a sample test to check that the proper message has been added to the ErrorContext.

```
package waffle.controllers;

import static org.mockito.Matchers.argThat;
import static org.mockito.Mockito.doThrow;
import static org.mockito.Mockito.mock;
import static org.mockito.Mockito.verify;

import org.codehaus.waffle.validation.ErrorsContext;
import org.codehaus.waffle.validation.FieldErrorMessage;
import org.junit.Test;

import waffle.services.AuthenticationExeption;
import waffle.services.AuthenticationService;
import waffle.validators.UserLoginControllerValidator;

public class UserLoginControllerValidatorTest {

private static final String username = "test";
        private static final String password = "test";

@Test
        public void shouldAddAnUserNotFoundErrorWhenUserNotFoundWithTheService() throws Exception {
                // given
                AuthenticationService service = mock(AuthenticationService.class);
                UserLoginControllerValidator validator = new UserLoginControllerValidator(service);
                ErrorsContext errors = mock(ErrorsContext.class);

// when
                doThrow(new AuthenticationExeption("User not found")).when(service).login(username, password);
                validator.login(errors, username, password);

// then
                FieldErrorMessage expectedErrorMessage = new FieldErrorMessage("name", username, "User not found");
                verify(errors).addErrorMessage(argThat(new IsAnErrorMessageLike(expectedErrorMessage)));
        }

}
```

I’m, indeed, using [Mockito](http://code.google.com/p/mockito/) and IsAnErrorMessageLike is a custom [Hamcrest Matcher](http://code.google.com/p/hamcrest/), it looks like:

```
package waffle.controllers;

import org.codehaus.waffle.validation.ErrorMessage;
import org.codehaus.waffle.validation.FieldErrorMessage;
import org.hamcrest.BaseMatcher;
import org.hamcrest.Description;

public class IsAnErrorMessageLike extends BaseMatcher {

private final FieldErrorMessage fieldErrorMessage;

public IsAnErrorMessageLike(FieldErrorMessage fieldErrorMessage) {
            this.fieldErrorMessage = fieldErrorMessage;
    }

@Override
    public boolean matches(Object object) {
            if (object == null)
                    return false;
            if (!(object instanceof FieldErrorMessage))
                    return false;

FieldErrorMessage other = (FieldErrorMessage) object;

if (other.getMessage().equals(fieldErrorMessage.getMessage())
                            &amp;&amp; (other.getName().equals(fieldErrorMessage.getName()))
                            &amp;&amp; (other.getType().equals(fieldErrorMessage.getType()))
                            &amp;&amp; (other.getMessage().equals(fieldErrorMessage.getMessage()))                                
                            &amp;&amp; (other.getValue().equals(fieldErrorMessage.getValue())))
                    return true;

return false;
    }

@Override
    public void describeTo(Description description) {
            description.appendText(fieldErrorMessage.toString());
    }

}
```
