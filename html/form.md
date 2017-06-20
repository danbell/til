# Only inputs with a "name" attribute get passed in a form action

Consider the following: 
```jade
html
  head
  body
    form(action='/the-action' method='get')
      input#name(type='text' required='')
      button(type='submit')
```

On clicking the "submit" button, one might expect the following HTTP request to be made:
```
GET /the-action?name=some-value
```
However, this won't occur because the input needs to specify the "name" attribute:
```jade
html
  head
  body
    form(action='/the-action' method='get')
      input#name(name='name' type='text' required='')
      button(type='submit')
```