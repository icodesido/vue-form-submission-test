# first-proto

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

### 1. What would make this process easier in the future? 
```
As I don't know the flow of the process, hard to say. I'd add a remember me funcionality with localStorage for persistent data: title, name, address, maybe even collapsing them to shorten scrollability.
```
### 2. What would you do differently to your implementation if you had more time?
```
I would add some transitions to field borders as well as darkening the color of the corresponding legend.
I would add the error depending on error lenght underneath each corresponding field and scrolling to the first errored field.
I would add some waiting animation while the form is checked.
I would display the reference number is a nicer way, maybe as some kind of modal or replacing the form.

```
### 3. What testing did (or would) you do, and why?
```
Forms have 4 levels of 'testing': the html required attribute, checking the well-formedness of the data as you keyup or leave the field's focus, another level when submitting and a final check from the back end.
Unit testing of individual fields or the reference number would need requirements.  
```