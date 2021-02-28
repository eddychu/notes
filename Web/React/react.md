# Context is just global varibale

To understand the usage of context in React, let's start with a metaphor. You have a function called ***function app(arguments)***. When this function requires some external information, we would provide it in the arguments. But sometimes the same data supply to this function need to be shared with many other functions in the same code base. we will try to make this common arguments globally accessible, so that we don't need to pass it down one by one.

In the "context" of React, a component is nothing but a function, the props are the arguments, so context is just a global variable (for all its consumer components). 

***I use component here loosely but it just means for functional component.While the usage of context in class component is similar, functional component is easier to understand, especially with the metaphor above. btw, functional components are the "ideal" way to use react anyway.***

## Why Use Context

Because the strict rule of one direction data flow in React philosophy, data is passed only from parent to children via props. Often times we find ourselves trapped into a situation that some props are required by many components, and even componets' children and grandchildren. Pass them down one by one greatly reduced the reusability of our component.

Here is the example to illustrate:

```javascript
const App = () => <Home user={user} />
const Home = ({user}) => <Timeline user={user} />
const Timeline = ({user}) => (
    <div>
        <LatestPost user={user} />
        <Recommend user={user} />
        <Notification user={user} />
    </div>
)
// ...
```
Because all the child components require the user information, instead of passing them down this way,  we will be much better off just provide it in the context.

## How to Use Context

The context api in react is pretty straightforward:
1. create Context with default context value
2. find the common ancestor component of the components in which context is used.
3. wrap the common ancestor in Provider container component.
4. access context value in component through Consumer container or (even better with hooks) useContext() function.

```javascript
const UserContext = React.createContext({username: "admin", isAuthed: true })

const Home = () => <UserContext.Provider> <Timeline /> </UserContext.Provider>

// Consumer component requires function as a child
const TimeLine = () => {
    return <UserContext.Consumer>
            {user => <Recomnend user={user} />}
           </UserContext.Consumer>
}

// or with hooks
const TimeLine = () => {
    const user = useContext(UserContext)
    return <Recommend user={user} />
}

```

***While context makes it much easier to share data between multiple React components, it should be used with causion. Think context as a global variable helps, because we should only use global varibale when it is absolutely necessary.***










why?


how?


what?
