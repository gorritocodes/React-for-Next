# Props

So far, if you were to reuse your \<Header /> component, it would display the same content both times.

```jsx
function Header() {
	return <h1>Develop. Preview. Ship. 🚀</h1>;
}

function HomePage() {
	return (
		<div>
			<Header />
			<Header />
		</div>
	);
}
```

But what if you want to pass different text or you don't know the information ahead of time because you're fetching data from an external source?

Regular HTML elements have attributes that you can use to pass pieces of information that change the behavior of those elements. For example, changing the src attribute of an \<img> element changes the image that is shown. Changing the href attribute of an \<a> tag changes the destination of the link.

In the same way, you can pass pieces of information as properties to React components. These are called props.

![](props.avif)

Similar to a JavaScript function, you can design components that accept custom arguments (or props) that change the component's behavior or what is visibly shown when it's rendered to the screen. Then, you can pass down these props from parent components to child components.

> In React, data flows down the component tree. This is referred to as one-way data flow. State, which will be discussed in the next section, can be passed from parent to child components as props.

## Using props

In your HomePage component, you can pass a custom title prop to the Header component, just like you'd pass HTML attributes:

```jsx
function HomePage() {
	return (
		<div>
			<Header title='React 💙' />
		</div>
	);
}
```

And Header, the child component, can accept those props as its first function parameter:

```jsx
function Header(props) {
	return <h1>Develop. Preview. Ship. 🚀</h1>;
}
```

If you console.log() props, you can see that it's an object with a title property.

```jsx
function Header(props) {
	console.log(props); // { title: "React 💙" }
	return <h1>React 💙</h1>;
}
```

Since props is an object, you can use object destructuring to explicitly name the values of props inside your function parameters:

```jsx
function Header({ title }) {
	console.log(title); // "React 💙"
	return <h1>React 💙</h1>;
}
```

Then you can replace the content of the \<h1> tag with your title variable.

```jsx
function Header({ title }) {
	console.log(title);
	return <h1>title</h1>;
}
```

If you open your project in the browser, you will see that it is displaying the actual word "title". This is because React thinks you're intending to render a plain text string to the DOM.

You need a way to denote to React that this is a JavaScript variable.

## Using variables in JSX

To use the variable you defined, you can use curly braces { }, a special JSX syntax that allows you to write regular JavaScript directly inside your JSX markup.

```jsx
function Header({ title }) {
	console.log(title);
	return <h1>{title}</h1>;
}
```

You can think of curly braces as a way to enter "JavaScript land" while you are in "JSX land". You can add any JavaScript expression (something that evaluates to a single value) inside curly braces. For example:

### An object property with dot notation.

```jsx
function Header(props) {
	return <h1>{props.title}</h1>;
}
```

### A template literal:

```jsx
function Header({ title }) {
	return <h1>{`Cool ${title}`}</h1>;
}
```

### The returned value of a function.

```jsx
function createTitle(title) {
	if (title) {
		return title;
	} else {
		return "Default title";
	}
}

function Header({ title }) {
	return <h1>{createTitle(title)}</h1>;
}
```

### Or ternary operators.

```jsx
function Header({ title }) {
	return <h1>{title ? title : "Default Title"}</h1>;
}
```

You can now pass any string to your title prop, and since you've accounted for the default case in your component with the ternary operator, you could even not pass a title prop at all:

```jsx
function Header({ title }) {
	return <h1>{title ? title : "Default title"}</h1>;
}

function HomePage() {
	return (
		<div>
			<Header />
		</div>
	);
}
```

Your component now accepts a generic title prop which you can reuse in different parts of your application. All you need to do is change the title:

```jsx
function HomePage() {
	return (
		<div>
			<Header title='React 💙' />
			<Header title='A new title' />
		</div>
	);
}
```

### Iterating through lists

It's common to have data that you need to show as a list. You can use array methods to manipulate your data and generate UI elements that are identical in style but hold different pieces of information.

> React is unopinionated when it comes to data fetching, meaning you can choose whichever solution best suits your needs. Later on, we'll discuss data fetching options in Next.js. But for now, you can use a simple array to represent data.

### Add an array of names to your HomePage component:

```jsx
function HomePage() {
	const names = ["Ada Lovelace", "Grace Hopper", "Margaret Hamilton"];

	return (
		<div>
			<Header title='Develop. Preview. Ship. 🚀' />
		</div>
	);
}
```

### You can then use the array.map() method to iterate over the array and use an arrow function to map a name to a list item:

```jsx
function HomePage() {
	const names = ["Ada Lovelace", "Grace Hopper", "Margaret Hamilton"];

	return (
		<div>
			<Header title='Develop. Preview. Ship. 🚀' />
			<ul>
				{names.map((name) => (
					<li>{name}</li>
				))}
			</ul>
		</div>
	);
}
```

Notice how you've used curly braces to weave in and out of "JavaScript" and "JSX" land.

If you run this code, React will give us a warning about a missing key prop. This is because React needs something to uniquely identify items in an array so it knows which elements to update in the DOM.

You can use the names for now since they are currently unique, but it's recommended to use something guaranteed to be unique, like an item ID.

```jsx
function HomePage() {
	const names = ["Ada Lovelace", "Grace Hopper", "Margaret Hamilton"];

	return (
		<div>
			<Header title='Develop. Preview. Ship. 🚀' />
			<ul>
				{names.map((name) => (
					<li key={name}>{name}</li>
				))}
			</ul>
		</div>
	);
}
```

Additional Resources:

- [Passing props to a component](https://react.dev/learn/passing-props-to-a-component)
- [Rendering lists](https://react.dev/learn/rendering-lists)
- [Conditional rendering](https://react.dev/learn/conditional-rendering)
