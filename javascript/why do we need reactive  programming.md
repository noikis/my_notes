
## Promises are not enough

```javascript
const btn = document.querySelector('#btn') 
btn.addEventListener('click', async (event) => {
  const { className } = event.target
  const p1 = new Promise((resolve, reject ) => {
    if (/foobar/.test(className))  { 
      resolve(className); 
    }
    else  { 
      reject();
    }
  })

  p1.then((className => { console.log(className) } ))
})
```
In the code snippet below a promise is created on each click event.
But there the principle `seperation of consurnes` was violated, because the creation of the promise (  `new Promise((resolve, reject )` ) and it consumption  ` resolve(className) ` hapen in the same place.

We need higher order patterns for handling stream of events that uses promises.

## A definition to Observables ( Reactive programming )

An observable is an attachment to an event stream, that produces a promise for each event. 
It takes care of the complexity of creating the events and promises and seperating them, so that we can define the response to an event as a chain of promises.
In that way we can define the stream producing the event and the consumer in different places.


```javascript
const btn = document.querySelector('#btn') 
const observer = rx.Observable.fromEvent(btn, "click")

observer
  .map((event) => event.target.className)
  .filter((className) => /foobar/.test(className) )
  .distinctUntilChanged()
  .subscribe((data) =>  {
    const className = data[1];
    console.log(className);
  })

```

Fundamentally observables are a way to `subscribe` to a chain of events asynchronously.
