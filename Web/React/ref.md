The value of the ref differs depending on the type of the node:

When the ref attribute is used on an HTML element, the ref created in the constructor with React.createRef() receives the underlying DOM element as its current property.
When the ref attribute is used on a custom class component, the ref object receives the mounted instance of the component as its current.
You may not use the ref attribute on function components because they don’t have instances.

React will assign the current property with the DOM element when the component mounts, and assign it back to null when it unmounts. ref updates happen before componentDidMount or componentDidUpdate lifecycle methods.



use callback pattern or the createRef api

If the ref callback is defined as an inline function, it will get called twice during updates, first with null and then again with the DOM element. This is because a new instance of the function is created with each render, so React needs to clear the old ref and set up the new one. You can avoid this by defining the ref callback as a bound method on the class, but note that it shouldn’t matter in most cases.



when to use forwardRef

Managing focus, text selection, or media playback
Let’s imagine you have an input component. In some parts of your application, you may want the cursor focused on it when a user clicks a button. It makes more sense to modify only that particular instance of the input component without changing the state (via refs), rather than changing the state (via props) which will cause the component to re-render every-time. Similarly, we can use refs to control the state of music or video players (pause, play, stop) without them re-rendering anytime we click a button (change the state).

```
const SampleButton = React.forwardRef((props, ref) => (
  <button ref={ref} className="button">
    {props.children}
  </button>
));

const ref = React.createRef();
<SampleButton ref={ref}>Click me!</SampleButton>;
```
Now that we’ve wrapped the SampleButton component with the forwardRef method, components using it can get a ref to the underlying button DOM node and access it if necessary —just like if they used a DOM button directly.