setState

don't rely on this.state to reflect the new value immediately after calling setState.

```javascript
class App extends component{
    increment() {
        this.setState({count: this.state.count + 1})
    }

    repeatIncrement() {
        this.increment();
        this.increment();
        this.increment();
    }

    // When React re-renders the component, `this.state.count` will be 1, but you expected 3.
}

```

to ensure the state is updated based on the current value. pass a function instead of an object to setState.


```javascript
class App extends component{
    increment() {
        this.setState((state) => {
            return {count: state.count + 1}
        })
    }

    repeatIncrement() {
        this.increment();
        this.increment();
        this.increment();
    }

    // If you read `this.state.count` now, it would still be 0.
    // But when React re-renders the component, it will be 3.
}

```


when if both parent and child component call setState during a click event, Child isn't re-rendered twice. Instead, React “flushes” the state updates at the end of the browser event. This results in significant performance improvements in larger apps.


setState is batched

As explained in the previous section, React intentionally “waits” until all components call setState() in their event handlers before starting to re-render. This boosts performance by avoiding unnecessary re-renders.


props (short for “properties”) and state are both plain JavaScript objects. While both hold information that influences the output of render, they are different in one important way: props get passed to the component (similar to function parameters) whereas state is managed within the component (similar to variables declared within a function)