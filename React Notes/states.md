# State

Adding Interactivity with State
Let's explore how React helps us add interactivity with state and event handlers.

As an example, let's create a like button inside your HomePage component. First, add a button element inside the return() statement:

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

			<button>Like</button>
		</div>
	);
}
```

Listening to events
To make the button do something when clicked, you can make use of the onClick event.

```jsx
function HomePage() {
  // ...
  return (
    <div>
      {/* ... */}
      <button onClick={}>Like</button>
    </div>
  );
}
```

In React, event names are camelCased. The onClick event is one of many possible events you can use to respond to user interaction. For example, you can use onChange for input fields or onSubmit for forms.

Handling events
You can define a function to "handle" events whenever they are triggered. Create a function before the return statement called handleClick():

```jsx
function HomePage() {
  // ...

  function handleClick() {
    console.log("increment like count")
  }

  return (
    <div>
      {/* ... */}
	  <button onClick={}>Like</button>
    </div>
     )
   }
```

Then, you can call the handleClick function when the onClick event is triggered:

```jsx
function HomePage() {
	// 	...
	function handleClick() {
		console.log("increment like count");
	}

	return (
		<div>
			{/* ... */}
			<button onClick={handleClick}>Like</button>
		</div>
	);
}
```

State and hooks
React has a set of functions called hooks. Hooks allow you to add additional logic such as state to your components. You can think of state as any information in your UI that changes over time, usually triggered by user interaction.

Examples of state
You can use state to store and increment the number of times a user has clicked the like button. In fact, this is what the React hook to manage state is called: useState( )

```jsx
function HomePage() {
	React.useState();
}
```

useState( ) returns an array, and you can access and use those array values inside your component using array destructuring:

```jsx
function HomePage() {
	const [] = React.useState();

	// ...
}
```

The first item in the array is the state value, which you can name anything. It's recommended to name it something descriptive:

```jsx
function HomePage() {
	const [likes] = React.useState();

	// ...
}
```

The second item in the array is a function to update the value. You can name the update function anything, but it's common to prefix it with set followed by the name of the state variable you're updating:

```jsx
function HomePage() {
	const [likes, setLikes] = React.useState();

	// ...
}
```

You can also take the opportunity to add the initial value of your likes state: zero.

```jsx
function HomePage() {
	const [likes, setLikes] = React.useState(0);
}
```

Then, you can check the initial state is working by using the state variable inside your component.

```jsx
function HomePage() {
	// ...
	const [likes, setLikes] = React.useState(0);

	return (
		// ...
		<button onClick={handleClick}>Like({likes})</button>
	);
}
```

Finally, you can call your state updater function, setLikes in your HomePage component, let's add it inside the handleClick() function you previously defined:

```jsx
function HomePage() {
	// ...
	const [likes, setLikes] = React.useState(0);

	function handleClick() {
		setLikes(likes + 1);
	}

	return (
		<div>
			{/* ... */}
			<button onClick={handleClick}>Likes ({likes})</button>
		</div>
	);
}
```

Clicking the button will now call the handleClick function, which calls the setLikes state updater function with a single argument of the current number of likes + 1.

> Unlike props which are passed to components as the first function parameter, the state is initiated and stored within a component. You can pass the state information to children components as props, but the logic for updating the state should be kept within the component where state was initially created.

Managing State
This was only an introduction to state, and there's more you can learn about managing state and data flow in your React applications. To learn more, we recommend you go through the Adding Interactivity and Managing State sections in the React Documentation.

Additional Resources:

- [State: A component's memory](https://react.dev/learn/state-a-components-memory)
- [Meet your first hook](https://react.dev/learn/state-a-components-memory#meet-your-first-hook)
- [Responding to Events](https://react.dev/learn/responding-to-events)
