# React Best Practices

### (Rishi's Notes)
https://www.potterapi.com/v1/characters?key=1
```css
#pentagon {
    position: relative;
    width: 54px;
    border-width: 50px 18px 0;
    border-style: solid;
    border-color: red transparent;
}
#pentagon:before {
    content: "";
    position: absolute;
    height: 0;
    width: 0;
    top: -85px;
    left: -18px;
    border-width: 0 45px 35px;
    border-style: solid;
    border-color: transparent transparent red;
}
```


### 1. NPX

`npx create-react-app app-name`

Why? Cause my old c-r-a was waaay out of date.


### 2. Functional vs. Class-Based Components

Rule: Only use a class-based component if you need state or a lifecycle method.

### 3. If you're fetching, do it after `componentDidMount()`

```js
class MyComp extends React.Component {
  componentDidMount() {
    fetch(someUrl)
      .then(resp => resp.json())
      .then(resp => console.log(resp))
  }
}
```

### 4. JS Objects where the key is a variable name

```js
const hello = "world"
{ hello }
// is the same as
{ hello: hello } //which equals { hello: 'world' }
```

### 5. Destructuring Props

```js
// this.props looks like { hello: 'world', goodnight: 'sweet prince' }

const {
  hello,
  goodnight
} = this.props

// now the const hello = 'world', and goodnight = 'sweet prince'
```

you can also do it inline in a js functional component as so:
```js
const component = ({ hello, goodnight }) => {
  return <p>{hello}</p>
}
```

### 6. Spread Syntax

You can pass an entire object's keys as props using the ES6 Spread syntax.

```js
// if props are { hi: 'bye', cool: 'dude' }
<Component {...this.props} />
// the props passed in will have the same structure
```

### 7. Fragments
In react, every component must have a div parent. UNLESS! You can use `Fragment`
```js
const myComponent = (props) => {
  return <React.Fragment>
    <div className="div1" />
    <div className="div2" />
  </React.Fragment>
}
```
