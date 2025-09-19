## Components (Components as Building Blocks)
- React applications are entirely made out of components.
- **Building Blocks** of user interfaces in React.
- Piece of UI that has its own **Data**, **Logic**, and **Appearance** (how it works and looks).
- We build complex UIs by **Building Multiple Components** and **Combining** them.
- Components can be **Reused**, **Nested** inside each other, and **Pass Data** between them.

---

**Component** -> Component is a piece of user interface(UI).

Components are the most fundamental concept in React, simply because React applications are, in fact, entirely made out of components. therefore we say that components are the building blocks of any user interface. 

Basically all React does is to take components and draw them onto a web-page, so onto a user interface (UI).

React renders a view for each component, and all these views together make up the user interface. So we can also think of a component as being a piece of the use interface.

One key property of components is that each component has its own **Data**, **JavaScript logic**, and **Appearance**. So basically, each component describes how it works and what it looks like, which makes them such a great way of building user interfaces.

One thing that we do all the time is to place components inside of other components, or in other words, we **Nest** components inside each other. So **Nesting** Components is a key aspect of using components in React along with the component reusability.

Components can be **Reused**, **Nested** inside each other, and **Pass Data** between them.

One crucial skill is breaking a design into its components.
One thing that helps with that and with analyzing the components that we create is a **Component Tree**. 

So **Component Tree** shows the hierarchy that exists between the components that make up the user interface, and it makes it really easy to understand how all of these components are **Nested** inside each other, and how the relate to one another. We can also clearly see relationships between components.

## What is JSX
- JSX is a **Declarative** syntax to **Describe** what components **look like** and **how they work**.
- Components must **return** a block of JSX.
- JSX is an Extension of JavaScript that allows us to **embed JavaScript, CSS and React components into HTML**.
- Each JSX element is **converted** to a `React.createElement` function call.
- We could use React **without JSX**.

---

**JSX** -> JSX is a **Declarative** syntax, that we use to describe what components look like and how they work based on their data and logic. So it is all about components appearance.

Each component must return one block of JSX, which React will then use to render the component on the UI.
JSX is an extension of JavaScript, which allows us to **combine parts of HTML, CSS and JavaScript all into one block of code**.
basically, we can write HTML and embed some pieces of JavaScript where necessary.

Behind the scenes, all the JSX that we write is converted into many nested `React.createElement` function calls. and these function calls are what in the end, create the HTML elements that we see on the screen. 
This means that we could actually use React without JSX at all. We could just manually write these `React.createElement` functions instead of JSX, but it makes the Code really hard to read and to understand.

### Imperative
- Manual DOM element selections and DOM traversing.
- Step-by-Step DOM mutations until we reach the desired UI.

---

**Imperative** -> So in the **Imperative** approach, we basically tell the browser exactly how to do things. _(How to do things)_

When we try to build UIs using vanilla JavaScript, we will by default use an **Imperative** approach. This means that we manually select elements, traverse the DOM, and attach event handlers to elements. Then each time something happens in the app like a click on the button, we give the browser a step-by-step instructions on how to mutate those thumb elements until we reach the desired updated UI. 

### Declarative
- Describe what UI should look like using JSX, **based on the current data**.
- React is an **Abstraction** away from DOM: **we never touch the DOM**.
- Instead, we think of the UI as a **reflection of the current data**.

---

**Declarative** -> A declarative approach is to simply describe what the UI should look like at all times, always based on the current data that's in the component. _(What we want)_

This data is **Props** and **State**. Basically, we use JSX to describe the UI based on **props** and **state**, So the data that's currently in the component, and all that happens without any DOM manipulation at all.

React is basically a huge abstraction away from the DOM. Instead, we think of the UI as a reflection of the current data and let React automatically synchronize the UI with that data.

Piece of JSX is like any other JavaScript Expression, JSX produces a JavaScript Expression.

```javascript
const el = <h1>Hello React!</h1>; 
const el = React.createElement("h1", null, "Hello React!")
```

### The Rules of JSX
**General JSX Rules**:
- JSX works essentially like HTML, but we can enter "**JavaScript mode**" by using `{}` (for text or attributes).
- We can place **JavaScript expressions** inside `{}`. Examples: reference variables, create arrays or objects, `[].map()`, ternary operator.
- Statements are **not allowed** (if/else, for, switch).
- JSX produces a **JavaScript expression**.
	1. We can place **other pieces of JSX** inside `{}`.
	2. We can write JSX **anywhere** inside a component (in `if/else`, assign to variables, pass it into functions).
- A piece of JSX can only have **one root element**. If you need more, use `<React.Fragment>` (or the short <>).

**Differences between React JSX and HTML**:
- `className` instead of HTML's class.
- `htmlFor` instead of HTML's for.
- Every tag needs to be **closed**. Examples: `<img />` or `<br />`.
- All event handlers and other properties need to be **camelCased**. Examples: `onClick` or `onMouseOver`.
- **Exception**: `aria-*` and `data-*` are written with dashed like in HTML.
- CSS inline styles are written like this: `{{<style>}}` (to reference a variable, and then an object).
- CSS property names also **camelCased**.
- Comments need to be in `{}` (because they are JS).

## Props
- Props are used to pass data from **parent components** to **child components** (down the component tree).
- Essential tool to **configure** and **customize** components (like function parameters).
- With props, parent components **control** how child components look and work.
- **Anything** can be passed as props: single values, arrays, objects, functions, even other components.
 
--- 

**Props** -> So we can imagine props as settings that we can use to make a parent component control how its child component should look like and how it should work. So in that regard, props are just like arguments passed to regular JavaScript functions. 

Props are short for **Properties**.

We use props in React to pass data from parent components to child components. So essentially to pass information down the component tree. This means that essentially we use props to communicate between parent and child components. Therefore, props are an essential React tool to configure and also to customize components.

Also we can pass anything into JavaScript functions, and same is actually true for props too. So we can pass any type of value as a prop.

**Props are READ-ONLY**!

So the data that React uses to render a component is made out of props and state.
- **State** -> State is **internal** data that can be updated by the **component's** logic.
- **Props** -> Props is data coming from the **outside**, and can **only** be updated by the parent component.

This brings us to one of the few strict rules that React gives us:
 - Props are read-only, they are **immutable**.
 - If you need to mutate props, you actually **need state**.

Props are just an object. Therefore, if we change the props object in your component you would also affect the parent component. So when you copy an object and mutate the copy, the original object will also be mutated. 

Now, if you change an object that is located outside of the component function, that function has then created a so-called side effect. So components have to be pure in terms of their props and state, because this allows React to optimize our application and it avoids some strange bugs that can appear when you manipulate external data.

Props are immutable because:
- Mutating props would affect parent, creating **side effects** (not pure).
- Components have to be **pure functions** in terms of props and state.
- This allows React to optimize apps, avoid bugs, make apps predictable.

## Children Prop
- The children prop allow us **to pass JSX into an element** (besides regular props).
- Essential tool to make **reusable** and **configurable** components (especially component **content**).
- Really useful for **generic** components that **don't know their content** before being used (e.g. modal).

--- 

**Children Props** -> **Children Props** refer to a special prop in React components that acts as a **placeholder** for any JSX content passed between a component's opening and closing tags. This allows the component to be dynamically filled with **arbitrary elements, components, or text** provided by its parent. The `children` prop is especially useful for creating **flexible, reusable components** that can wrap and render different types of content as needed.

Is an Empty **"hole"** that can be filled by **any JSX the component receives** as children. 

Children of a Component, is accessible through `props.children` key/property owned by the `props` object. 

So by using the children prop in the component, we basically left an empty "hole" right in the component that we could then fill with any JSX markup that the component receives as children.

We can pass these **Children Props** by including the component in some JSX, instead of immediately closing the element, we can write some more JSX into that element. So just like we can write any HTML markup inside other HTML elements.

So just like an HTML elements, we can write anything that we want between the opening and the closing tag of the component that we are using.

```JSX
function Items(){
	<div>
		<Item arg1="str">
			<span>This is were we write Children Props</span>
		</Item>
	</div>
}

function Item(props){
	return props.children
}
```


## State in React
- **State** is the most important concept in React.
- Data that a component **can hold over time**, necessary for information that it needs to **remember** throughout the app's lifecycle.
- **Component's memory**.
- "**State variable**" / "**Piece of state**": A single variable in a component (component state).
- Updating **component state** triggers React to **re-render the component**.

---

**State** -> Data that a component **can hold over time**, necessary for information that it needs to **remember** throughout the app's lifecycle.

So state is basically data, that a component can hold over time, and we use it for information that a component need to remember throughout its lifecycle. Therefore, we can think of state as being the memory of a component. 

State is **internal** data that can be updated by the **component's** logic. State is basically **internal** component data that can be updated by the **component's** logic.

Without a doubt **State** is the most important concept in React. So everything basically revolves around state in React.

So a piece of state, or a state variable, is just one single actual variable in the component that we can define in our Code. on the other hand, the term state itself is more about the entire state that the component is in, like the entire condition at a certain point in time.

So, basically, the general term state is all the pieces of state together.

The most important aspect of state is the fact that updating state triggers React to re-render the component. 
So, whenever we update a piece of state in a component, this will make React re-render that component in the user interface. So it will create a new updated view for that component. 
A component's view is basically just the component visually rendered on the screen, so in the user interface.

**View** -> When one single component is rendered, we call that a view. All the views combined together then make up the final user interface.

So state is how React keeps the user interface in sync with data. We change the state, we change the UI.

### The Mechanics of State
- We don't do direct DOM manipulations (Because React is **declarative**).
- In React, a view is updated by **re-rendering** the component.
- State is preserved ed throughout re-renders.
- A component is re-rendered when its state is updated.
- So to update a view, we update state.

---

In React we do not manipulate the DOM directly whenever we update a component's view. So React is declarative, not imperative, and so we never touch the DOM in our code.

React updates a component view by re-rendering that entire component whenever the underlying data changes.

Re-Rendering basically means that React calls the component function again, So each time the component is rendered. So conceptually we can imagine this as React removing the entire view and replacing it with a new one each time a re-render needs to happen.

React preserves the component state throughout re-renders, and so even though a component can be rendered and re-rendered time and time again, the state will not be reset unless the component disappears from the UI entirely, which is what we call **unmounting**.

**Unmounting** -> Unmounting is when a component entirely disappears from the user interface.

_**It is when state is updated that a component is automatically re-rendered**_. When react sees/notices that state has been changed, it'll automatically re-render the component, which will result in an update view for this component.

The conclusion of all this is that as React developers, whenever we want to update a component view, we update its state, and so React will then react to that update and do its thing.

React reacts to state changes by re-rendering the user interface.

### More Thoughts About State + State Guidelines
#### One Component, One State
- Each component has and manages **its own state**, no matter how many times we render the same component.

---

Each component really has, and manages, its own state. So, even if we render the same component multiple times on one page, each of these component instances will operate independently from all the other ones. 
If we change the state in one of the components, that won't affect the other components at all. State really is isolated inside of each component.

#### UI as a Function of State
- With state, we view UI as a **reflection of data changing over time**.
- We **describe that reflection** of data using state, event handlers and JSX.

---

We can basically think of the entire application view, so, the entire user interface, as a function of state. 
In other words, the entire UI is always a representation of all the current states in all components.

A React application is fundamentally all about changing state over time, and also, correctly displaying that state at all times.

So, instead of viewing a UI as explicit DOM manipulations, with state, we now view a UI as a reflection of data changing over time. We describe that reflection of data using state, event handlers, and JSX. We describe the UI, React does the rest.

#### Practical Guidelines About State
- Use a state variable for any data that the component should keep track of ("remember") over time. **This is data that will change at some point**. In Vanilla JS, that's a `let` variable, or an `[]` or `{}`.
- Whenever you want something in the component to be **dynamic**, create a piece of state related to that "thing", and update the state when the "thing" should change (aka "be dynamic").
	- **Example**: A _modal window can be open or closed. So we create a state variable `isOpen` that tracks whether the modal is open or not. On `isOpne = true` we display the window, on `isOpen = false` we hide it_.
- If we want to change the way a component looks, or the data it displays, **update its state**. This usually happens in an **event handler** function.
- When building a component, imagine its view as a **reflection of state changing over time**.
- For data that should not trigger component re-renders, **don't use state**. Use a regular variable instead. This is a common **beginner mistake**.

### Summary
- State allows developers to:
	1. Update the components's view (by re-rendering it).
	2. Persist local variables between renders.

## Derived State
**Derived State** -> State that is computed from an existing piece of state or from props. So, essentially, derived state is simply state that is computed from another existing piece of state or also from props.

Most of the time we can not derive state, but whenever we have a situation when one state can easily be computed from another, always prefer derived state. So, don't create two state variables if you actually only need one.

### Examples
**Bad Example**: This makes us update the state **3** times, which causes multiple unnecessary re-renders of the whole component.
```JavaScript
const [cart, setCart] = useState([
	{name: "JavaScript Course", price: 15.99},
	{name: "Node.js Bootcamp", price: 14.99}
]);
const [numItems, setNumItems] = useState(2);
const [totalPrice, setTotalPrice] = useState(30.98);
```


**Deriving State**: Data is calculated without extra change in the state, which refrains us from Re-Rendering for no reason. 
```JavaScript
const [cart, setCart] = useState([
	{name: "JavaScript Course", price: 15.99},
	{name: "Node.js Bootcamp", price: 14.99}
]);
const numItems = cart.length;
const totalPrice = cart.reduce((acc, cur) => acc + cur.price, 0);
```


#### Bad
- Three separate pieces of state, even thought `numItems` and `totalPrice` depend on cart.
- Need to keep them in sync (update together).
- 3 state updates will cause 3 re-renders.

#### Good
- Just regular variables, no `useState`.
- `cart` state is the **single source of truth** for this related data.
- Works because re-rendering component will **automatically re-calculate** derived state.

## Difference between State and Props
### State
- **Internal** data, owned by component.
- Component "_memory_".
- Can be updated by the component itself.
- Updating state causes component to re-render.
- Used to make components interactive.

--- 

**State** -> State is **internal** data. So data that is owned by the component in which it is declared.

State can be thought of as the component's memory, because it can hold data over time, so across multiple re-renders. 

State can be updated by the component itself, and this will then cause the component to be re-rendered by React. 
Therefore, we use this mechanism of state to make components interactive.

State is used by developers to make components interactive.

### Props
- **External** data, owned by parent component.
- Similar to function parameters.
- Read-Only.
- **Receiving new props causes component to re-render**. Usually when the parent's state has been updated.
- Used by parent to configure child component ("_settings_").

--- 

**Props** -> Props is **external** data. So data that is owned by the parent component, and we can think of props as function parameters. 

So as communication channel between parent and child components where parents can pass data into children. 

**Props are READ only**, so they cannot be modified by the component that is receiving them. 
When the child component receives new updated props, that will actually also cause the component to re-render, 

Props are used to give the parent component the ability to configure their child components. 
So basically props can be seen as settings in child component, which the parent component can define as they wish.

## One-Way Data Flow
**One-Way Data Flow** -> One-Way Data Flow means that in React applications, data can only be passed from parent to child components, which happens by using props. 
So in other words, data can flow from parents to children, but never the opposite way. Therefore we have a one way data flow, so only from top to bottom of the component tree.

React uses a so-called one-way data flow. Meaning that Data can only flow **down to children** (via props), not **sideways to siblings**.

There are multiple reasons to why React uses a one way data flow:
- makes applications more predictable and easier to understand.
- makes applications easier to debug, as we have more control over the data.
- is more performant.

## "Thinking in React" Is a Core Skill
- **React Mindset**.
- Thinking about components, state, data flow, effects, etc.
- Thinking in **state transitions**, not element mutations.
---

### "Thinking in React" as a Process
Not a Rigid Process.

1. Break the desired UI into **components** and establish the **component tree**.
2. Build a **static** version in React (without state).
3. Thinks about **state**:
	- When to use state.
	- Types of state: local vs global.
	- Where to place each piece of state.
4. Establish **data flow**:
	- One-Way data flow.
	- Child-to-Parent communication.
	- Accessing global state.

When we know how to "Think In React", we will be able to answer:
- How to break up a UI design into component?
- How to make some components reusable?
- How to assemble UI from reusable components?
- What pieces of state do I need for interactivity?
- Where to place state? (What component should "own" each piece of state?).

## Fundamentals of State Management
### What is State Management
**State Management** -> Deciding **when** to create pieces of state, what **types** of state are necessary, **where** to place each piece of state, and how data **flows** through the app.

So as we already know, we can use the `useState` function to create multiple pieces of state in order to track data that changes over the life cycle of an application.

### Types of State: Local VS Global State
In React, each piece of state is either a local state or a global state. 

#### Local State
- State needed **only by one or few components**.
- State is defined in a component and **only that component and child components** have access to it (by passing via props).

---

**Local State** -> Local state is state that is only needed in one component or any few different components, like child or sibling components.

We simply create a piece of local state using the `useState` function inside a certain component, and that piece of state is then only **accessible** to that exact component and maybe to its child components.

#### Global State
- State that **many components** might need.
- **Shared** state that is accessible to **every component** in the entire application.

---

**Global State** -> Global State is the state that many different components in the app might need access to. 
Therefore, when we define state as being global, that piece of state will become **accessible** to every single component in the entire app.

It is shared between all components, and therefore, we can also call this shared state. In practice, we can define global state using React's `Context API` or also an external global state management library like `Redux`.

### State: When and Where?
![[Pasted image 20250219140040.png]]


## Sharing State With Sibling Component (Lifting Up State)
**Lifting Up State** -> Lifting Up State simply means to place some state in a component that is a parent of both components that need the piece of state in question.

To give both components access to the state, we just simply pass it down using props.

By **lifting state up**, we have successfully **shared** one piece of state with multiple components in **different positions** in the component tree.

To update a state that is in the parent component from a child component, all we have to do is pass the setter function down as a prop to the components that need to update the state.

To share state between sibling components in React, we use a technique called **Lifting State Up**. Since sibling components cannot directly share state, the state must be moved to their closest common parent. The parent component then manages the state and passes it down as props to both siblings. To allow a child component to update the shared state, the parent also passes down the state setter function as a prop. This way, one sibling can modify the state, and the other can react to the updated value through the parent, ensuring synchronized state management across components.

**Child to Parent Communication (Inverse Data Flow)** -> Child updating parent state (data "flowing" **up**).

## Split UI Into Components
### Component Size
We always need some small components in any application, because they are highly reusable and have very low complexity, which is sometimes exactly what we need.
- **Some very small components are necessary**!
- Highly Reusable.
- Very low complexity.

Most apps will also have a few huge components, that are not meant to be reused. So in situations like this, don't worry about reusability or about needing to split this component up.
- **Most apps will have a few huge components**.
- Not meant to be reused (**Not a Problem**).

Finally, we have medium size components, which all have different degrees of size, reusability, and complexity.

The reusability range is pretty similar to the size range. Generally the smaller components are, the more reusable they will be. As components get bigger, they will become less reusable. Not all components are meant to be reusable.


#### Huge
- Too many **responsibilities**.
- Might need too many **props**.
- Hard to **reuse**.
- **Complex** code, hard to understand.

---

So we can classify every component based on its size, which means that we can place every component on this axis of component size. 

On one size we have really small components and on the other extreme, we have huge components. At many times, none of these extremes are ideal. 

So components are just like JavaScript functions, in the sense that if a function does too many different things, we should break it up into multiple functions. The same applies to React components. Another way in which it becomes apparent that a component is too large is when it needs to receive too many props in order to work properly.

In general these two problems make it very hard to reuse the component, also huge components generally contain a lot of code that might be complex and intertwined, which ultimately makes the whole component hard to understand and to use.

#### Small
- We end up with 100s of mini-components.
- Confusing Code Base.
- Too **abstracted**.

---

Most of the time creating small components would be  a terrible idea as well.

If we would build a UI or an entire app in this way, we would end up with hundreds if not thousands of mini-components. This would create a Code Base that is super confusing to navigate and to understand, and it would be way too abstracted.

So in a way, each new components that we create is an abstraction.

#### Balance Size
- Generally, we need to find the right balance between too specific and too broad.
- Logical Separation.
- Some are Reusable.
- Low Complexity.

---

Well, most of the time, the goal is to create components that strike the right balance between being too specific and too broad, or in other words, between being too small and being too big.

We can derive a couple of criteria that we can use to split a user interface into components.

First, when we decide which components we need to implement a certain UI, it's important that these components create a logical separation of the content, or even of the layout of a page.
We should also strive to make some of these components **Reusable** and ensure that each component has a **Single, Well-Defined Responsibility**.
Finally, there's one even more subjective criterion, which is personal Coding Style. So some people work better with smaller components, and some people just prefer larger components, and therefore, you need to create components in a way that works best for us.

1. Logical separation of content/layout
2. Reusability
3. Responsibilities / Complexity
4. Personal Coding Style

### When to Create a New Component?
- When in doubt, start with a relatively big component, then split it into smaller components as it becomes necessary.
- We can skip all of these if we're sure that we need to **Reuse**. But otherwise, you don't need to focus on reusability and complexity early on.

---

When we are creating a new component, and we're in doubt about what the component should include, just start with a relatively big component, but not huge component, and then split that bigger component into smaller components as it becomes **necessary**.

If we already know that we need a small and reusable component, such as a button, we can just skip all this and simply create a component. 
But otherwise we can just start big and don't need to focus on reusability or complexity at the very beginning. 

### Guidelines
#### 1. Logical Separation of Content/Layout
Questions to Ask:
- Does the component contain pieces of content or layout that **don't belong together**?

After writing our big component, we feel like the component contains some piece of Code, or the layout, that don't really belong together, then that meant that it's probably a good idea to create a new component.

#### 2. Reusability
Questions to Ask:
- Is it possible to reuse part of the component?
- Do we **want** or **need** to reuse it

If it's possible to reuse a part of your big component, and if you actually want or need to reuse that part, then we should take that Code and extract it into a new component.
 
#### 3. Responsibilities / Complexity
Questions to Ask: 
- Is the component doing too **many different things**?
- Does the component rely on too **many props**?
- Does the component have too **many pieces of state** and/or effects?
- Is the Code, including JSX, too **complex/confusing**?

Another sign that we should probably extract part of our component into a new one is that your component is doing way too many different things, or that it's relying onto many props.

So if our big component has too many pieces of state or effects, or if the Code is way too complex or too confusing, it might be once again time to create a new, smaller component.

#### 4. Personal Coding Style
Questions to Ask: Do we prefer **smaller** functions/component?

So it is important to feel productive when working with our components. So if we prefer smaller functions or component, just split up big component into smaller ones. but on the other hand, if we prefer big component, that's totally fine. It is all up to us.

### General Guidelines
- Be aware that creating a new component **creates a new abstraction**. Abstractions have a **cost**, because **more abstractions require more mental energy** to switch back and forth between components. So try not to create new components too early.
- Name a component according to **what it does** or **what it displays**. Don't be afraid of using long component names.
- Never declare a new component **inside another component**.
- **Co-Locate related component inside the same file**. Don't separate components into different files too early.
- it's completely normal that an app has components of **many different sizes**, including very small and huge ones.

---

So first off, we need to be aware that creating a new component creates a new abstraction. Abstractions have a cost, because having more abstractions requires more mental energy to think about different components and to switch back and forth between component. So we should try not to create new components too early if we can avoid it.

It is also important that we name a component according to what it does or what it displays. and don't be afraid of using long component names. that is completely normal in React Development.

We never, ever declare a new component inside another component. what we can do instead, when we have some related components is to Co-Locate these related components inside the same file.

Finally, and going back to our initial topic of component size, it's completely normal that an application has components of many different sizes, including some very small ones and some huge ones.

## Component Categories
Most of our components will **naturally** fall into **one of three categories**:
- Stateless / Presentational Components.
- Stateful Components.
- Structural Components.

We shouldn't force our components into one of these categories. these are all still normal react components in our Code. But we can categorize them in this way, when we think about components.

### Stateless / Presentational Components
- **No State**
- Can receive props and simply present received data or other content
- Usually **Small and Reusable**
---

**Stateless / Presentational Components** -> As the name says, these don't have any state. Usually, they are components that receive some props and then they simply present that data, or even some other content, and therefore the name presentational.

Many times these are quite small components, such as the logo, number of results.

### Stateful Components
- **Have State**
- Can still be **Reusable**
---

**Stateful Components** -> Simply components that do have state. 

Just because these components have state, that doesn't mean that they can't be highly reusable.

### Structural Components
- "**Pages**", "**Layouts**", or "**Screens**" of the app
- Result of **Composition**
- Can be **huge and non-reusable** (But don't have to)
---

**Structural Components** -> We can think of them as pages, layouts, or screens of the application, which are oftentimes the result of composing many smaller components together.

Structural Components can be large and non-reusable components, but they don't have to. Structural Components are sometimes quite small too. 
What matters is that they are responsible for providing some sort of structure to applications such as pages or layouts. Therefore, these components might not be present in really small apps.

## "Using" a Component
**"Using" a Component** -> When we **use** a component, we are essentially **invoking** (or calling) a component function inside another component. This means we are **embedding** one component within another, allowing us to **reuse UI elements** efficiently.

In practice, using a component is similar to calling a regular function, but instead of returning a simple value, it **returns JSX (UI elements)**. This helps in **breaking down the UI into smaller, reusable pieces**, making the code **more modular and maintainable**.

### Example
```jsx
// Using a Component
function Modal() {
	return (
		<div className="modal"
			<Success />
		</div>
	)
}
```

```jsx
function Success() {
	return <p>Well Done!</p>;
}
```

So let's say that we have this `Modal` component that we want to reuse, and also this `Success` component, and then we just use the `Success` component inside the modal Component like this.

However, when it comes to Reusability, this creates a big problem. that's because right now the `Success` Component really is inside of `Modal`. They're deeply linked together in the JSX right now, and therefore we cannot reuse this `Modal` component to display some other message inside of it, for example, an error message. 
In Order to solve this, we now bring in the technique of Component Composition, Where we **compose** the `Modal` and `Success` components together.

In this example, the `Success` component is really **tied** to the `Modal` and so that model might as well be called a `SuccessModal`, because we can't use it for anything else anymore.

## Components Composition
**Component Composition** -> Combining different components using the `children` prop (or explicitly defined props).

We use composition for two big reasons or in two important situations. First, when we want to create highly reusable and flexible components. Now, the second situation in which we can use composition is in order to fix a prop drilling problem. This is actually great for creating layouts.
1. Create highly reusable and flexible components.
2. Fix prop drilling (great for layouts).

This is only possible because components don't need to know their children in advance. Which allows us to leave these empty slots inside of them in the form of the `chilren` prop.

### Example
```JSX
// Function Composition
function Modal({children}) {
	return (
		<div className="modal"
			{children}
		</div>
	)
}
```

```JSX
function Success() {
	return <p>Well Done!</p>;
}
```

So this Component does not include a predefined component, but instead it accepts `children` with the `children` prop. 

So if we get our `Succes` component again, we can now basically just pass it into the modal by placing it between opening and closing tags when we use `Modal`.

With component composition, we simply pass the `Succes` component right into the `Modal` and **Composed** them together in this way. This works thanks to the `children` prop. We could have passed in any other component, which makes the `Modal` component highly reusable. 

So essentially when we do component composition, we leave this hole or this empty slot in the component, ready to be filled with any other component that we want.

## Props as an Component API
As we start working on our components, we should get into the mindset that any component is always created by someone, and always consumed by someone. 
Basically, the creator is the person building a component, and defining what props the component can accept. While the consume **uses** the component somewhere in the application, by specifying values for the props. 

If we have this mindset, we can think of the component's props as the public API of the component. So, as a component creator, when we choose what props the consumer is allowed to pass in, we are essentially defining the public interface of our component. 
And, at the same time, we are choosing how much complexity of the component we want to expose to the consumer of the API. Because, in the end, a component is basically just an abstraction. 
So, we are encapsulating a part of the UI and the associated logic into a component, and allow consumers to interact with that component via props. this is basically what creating a new component is.

**Component Consumer** -> Who uses the components.

**Component Creator** -> Who creates the components.

When we decide what props to allow in a component, we need to find a good balance on how strict we want to be. So about how many props we want to enable for configuration.

Too Little Props:
- Not **Flexible** Enough
- Might not be **useful**

Too Many Props:
- Too **hard** to use
- Exposing too much **complexity**
- **Hard-To-Write** Code

We need to find the right balance between too little and too many props, that works for both the consumer and the creator.

So, when deciding on the right API for our components, we try to strike the right balance between too little and too many props, and a balance that works well, for both the creator, and the consumer of the component, based on the project's needs.

If we really need to expose so many props, we make sure to at least provide some good default values for many of them.

## Component VS. Instance VS. Element
Let's begin by taking another look at components. 

**Components** -> So components are what we write in order to describe a piece of the user interface. and the component is just a regular JavaScript function, but it's a function that returns React Elements. So it returns an element tree. and we usually write these elements using the JSX syntax.
Now a component is a generic description of the UI. So we can essentially think of a component as a blueprint or a template, and it's out of this one blueprint or template that React then creates one or multiple component instances.
- **Description** of a piece of UI
- A component is a function that **return React Elements** (Element Tree), usually written as JSX
- "Blueprint" or "Template"

**Component Instance** -> React does this each time that we the component somewhere in our Code. Behind the scenes, this happens because React will call the component function n times, so one time for each instance.
So we can say that an instance is like the actual physical manifestations of a component living in our compenentry. while the component itself is really just a function that we wrote before being called and actually, it's each instance that holds its own state and props and that also has its own life cycle.
So basically, a component instance can be born, it can "live" for some time until it will eventually "die".
As React executes the Code in each of these instances, each of them will return one or more React Elements.
- Instances are created when we "**use**" components
- React internally calls component function
- Actual "**physical**" **manifestation** of a component
- Has its own state and props
- Has a **lifecycle** (can "be born", "live", and "die)

**React Element** -> Behind the Scenes, JSX will actually get converted to multiple `React.createElement` function calls. then as React calls these create element functions the result will be a React Element. So a React Element is basically the result of using a component in our Code. It's simply a big immutable JavaScript object that React keeps in memory.
A React Element basically contains all the information that is necessary in order to create DOM elements for the current component instance. So it's this React Element that will eventually be converted to actual DOM elements, and the painted onto the screen by the browser.
- JSX is converted to `React.createElement()` **function calls**
- A React element is the **result of these function calls**
- Information necessary to create **DOM Elements**

**DOM Element(HTML)** -> So based on all this, the DOM elements are the actual, final and visual representation of the components instance in the browser. 
- Actual **visual representation** of the component instance in the browser

It is not React Elements that are rendered to the DOM.
React Elements just live inside the React app and have nothing to do with the DOM. They are simply converted to DOM elements when they are painted on the screen in this final step.

## How Rendering Works
As we build our applications, what we really doing is building a bunch of components. We then use these components inside other components as many times as we want which will cause React to create one or more component instances of each component. So these are basically the actual physical components that live in our application and holds state and props.

As React calls each component instance, each JSX will produce a bunch of `React.createElement` function calls which in turn will produce a React Element for each component instance. So this React Element will ultimately be transformed to DOM elements and displayed as a user interface on the screen.

### How Components are Displayed on the Screen
#### Render Triggering Phase
**Render Is Triggered** -> This Process is started by React each time that a new render is triggered, most of the time by updating state somewhere in the application. So state changes trigger renders and so it makes sense that the next phase is the render phase.

So there are only two ways in which a render can be triggered. The first one is the very first time the application runs which is what we call the **initial render**. and the second is a state update happening in one or more component instances somewhere in the application which is what we call a **re-render**. 
The render process really is triggered for the entire application, not just for one single component. But that doesn't mean that the entire DOM is updated, because in React rendering is only about calling the component functions and figuring out what needs to change in the DOM later.
1. **Initial Render** of the application
2. **State is Updated** in one or more component instances (**re-render**)

The Render process is triggered for the **entire application**.

**In Practice**, it looks like React only re-renders the component where the state update happens, but that's not how it **works be
hind the scenes**.

Renders are **not** triggered immediately, but **scheduled** for when the JavaScript engine has some "free time". There is also batching of multiple `setState` calls in event handlers.

Now we know, that react **looks at the entire tree** whenever a render happens. 

Render is actually not triggered immediately after a state update happens. Instead, it's scheduled for when the JavaScript engine basically has some free time on its hands.

##### State Update Batching
- 
---

State Updates are batched. 

![[Pasted image 20250318205259.png]]

So here we have three pieces of state, defined using the `useState` hook, and we also have a `button` in the UI. Then whenever there is a click on the button, the event handler function named `reset` is called. In this function, the tree pieces of state, `answer`, `best`, and `solved` are basically reverted back to their original state. and therefore, this function is called `reset`.

Now let's now focus only on the event handler function.

###### WRONG: How React Updates multiple pieces of state
![[Pasted image 20250318205652.png]]

So we might think that, as React sees this `setAnswer` function call, it would update the state to the empty string as requested, and then trigger a re-render, and the commit phase, then it would move on to the next line, and do the same thing again, and finally do the entire thing for one more time for the third state update. 
So intuitively, we would think that, if there are three state variables being updated in this event handler, then React would re-render three times, however, this is actually not how it works.

So this is not how React updates multiple pieces of state in the same event handler function.

###### RIGHT: How React Updates multiple pieces of state
![[Pasted image 20250318210031.png]]

These state updates will actually get **batched** into just one state update for the entire event handler. So updating multiple pieces of state won't immediately cause a re-render for each update. Instead, all pieces of state inside the event handler are **updated in one go**. So they are batched, and only then will React trigger one single render and commit.

So if these state updates belong together, it really wouldn't make much sense to update screen three times. Doing so would also create two wasted renders, because we're not interested in the first two renders, only the final one, which already contains all the three state updates. Therefore, the fact that React automatically batches state updates in this way is yet another **performance optimization** that React gives us out of the box.

Batching state updates is extremely useful, but it can also have surprising results.

Let's turn out attention to this line of code `cosnsole.log(answer)` where we reference the `answer` state variable right after updating it.

![[Pasted image 20250318211456.png]]

The Component state is stored in the Fiber tree during the render phase. At this point in the code the render phase has not happened yet. So React is still reading the function line by line to figure out what state needs to be updated, but it hasn't actually updated the state yet, and it also hasn't re-rendered yet. 

**Stale** -> State not being fresh and updated.

So what this means is that, at this point of the code, the `answer` variable **will still hold the current state**. So the **state before the update**, even though we already told React to update it. So at this point we say that our state is **stale**, meaning that the state is no longer fresh and updated, because in fact, a state update will only be reflected in the state variable after the re-render. and so for this reason, we say that updating state in React is **asynchronous**.

It is **asynchronous** because React does not give us the updated state variable immediately after the `setAnswer` call, but only after the re-render has happened. 

Same thing also applies whenever there is only one piece of state being updated. So no matter how many state variables are being updated, the updated state is only available after the re-render, not immediately.

Sometimes we actually do need the new value immediately after updating it, and in the case, that we need the new value in order to update the same state again. or in other words, if we need to update state based on a previous state update in the same event handler, we can pass a callback function into the `setState` function instead of a single value.

###### Batching Beyond Event Handler Functions
![[Pasted image 20250318212042.png]]

For instance, we might want to run our `reset` function only a second after a click event, or we might want to run it after some data has been fetched. 

So before React 18, if this `reset` function was called by a timeout, or by a promise, state updates inside the function would not be batched. Instead, in these situations, React would actually update the state variables one by one, and therefore, in this case, render three times.
Another case is handling Native events using DOM methods such as `addEventListener`, where state updates also used to no be batched, but now they are.

If we are using React 18 version and higher we will now get automatic batching all the time, everywhere in our code.

#### Render Phase
**Render Phase** -> In this phase, React calls our component functions and figures out how it should update the DOM, so in order to reflect the latest state changes. However, it does actually not update the DOM in this phase. 
In React, rendering is **NOT** about updating the DOM or displaying elements on the screen. Rendering only happens **internally** inside React, it does not **produce visual changes**.

**Not Technically True** -> Rendering is not about the screen or the DOM or the view, it's just about calling component functions. we also know that whenever there is a re-render, React discards the old component view and replaces it with a brand new one. So the DOM will actually not be updated for the entire component instance.

So, at the beginning of the render phase React will go through the entire component tree, take all the component instances that triggered a re-render and actually render them, which simply means to call the corresponding component functions that we have written in our Code. This will create updated React elements which altogether make up the so-called **Virtual DOM**.

##### The Virtual DOM (React Element Tree)
- Tree of all React Elements created from all instances in the component tree
- Cheap and Fast to create multiple trees
- Nothing to do with "shadow DOM"
- Rendering a component will **cause all of its child components to be rendered as well** (no matter if props changed or not)
	- Necessary because React doesn't know whether children will be affected
- 
---

**Virtual DOM / React Element Tree** -> So, the Virtual DOM is just a tree of all React Elements created from all instances in the component tree. and it's relatively cheap and fast to create a tree, even if we need many iterations of it, because in the end it's just a JavaScript object.

So on the initial render, React will take the entire component tree and transform it into one big React Element which will basically be a React Element tree like this one.

![[Pasted image 20250313213957.png]]

This is what we call the **Virtual DOM**. 

Let's suppose that that there is gonna be a state update in component D, which will of course trigger a re-render. 
That means that React will call the function of component D again and place the new React Element in a new React Element Tree. So, in a new Virtual DOM. 

But now comes the very important part, whenever React renders a component, that render will cause all of its child components to be rendered as well. and that happens no matter if the props that we passed down have changed or not. If the updated components return one or more other components, those nested components will be re-rendered as well, all the way down the component tree. This means if we update the highest component in a component tree, in this example component A, then the entire application will actually be re-rendered.

React uses this strategy because it doesn't know beforehand whether an update in a component will affect the child components or not. and so by default, React prefers to play it safe and just render everything. 
Also, this does not mean that the entire DOM is updated. It's just a virtual DOM that will be recreated which is really not a big problem in small or medium sized applications.

**Current Fiber Tree** → Represents the UI as it exists in the DOM before state updates.

**Work-in-Progress (WIP) Fiber Tree** → A new version React builds when a state update occurs.

**Reconciliation Process** → Compares the WIP Fiber Tree with the Current Fiber Tree to determine changes.

**FIber** -> Fiber represents each component.

After this, the new Virtual DOM created after the state update will be reconciled with the current so-called **Fiber Tree** as it exists before the state update. This **Reconciliation** is done in React's **Reconciler** which is called **Fiber**. Then the results of this reconciliation process is gonna be an updated Fiber tree, so a tree that will eventually be used to write to the DOM.

##### What Is Reconciliation and Why Do We Need It?
- Writing to the DOM is (relatively) **slow**
- Usually only a **small part of the DOM** needs to be updated
- React **reuses** as much of the existing DOM as possible
- **Reconciliation**: Deciding which DOM elements actually need to be inserted, deleted, or updated, in order to reflect the latest state changes
---

**Reconciliation** -> Basically deciding exactly which DOM elements need to be inserted, deleted, or updated in order to reflect the latest state changes. 
The result of the reconciliation process is gonna be a list of DOM operations that are necessary to update the current DOM with a new state.

Reconciliation is processed by a **Reconciler** and we can say that the reconciler really is the engine of the React. It is the reconciler that allows us to never touch the **DOM directly** and instead simply tell React what the next snapshot of the UI should look like based on state. The current reconciler in React is called Fiber.

Writing to the DOM is not cheap and fast. It would be extremely inefficient and wasteful to always write the entire virtual DOM to the actual DOM each time that a render was triggered. 
Also, usually when the state changes somewhere in the app only a small portion of the DOM needs to be updated and the rest of the DOM that is already present can be reused.

On the initial render there is no way around creating the entire DOM from scratch but from there on, doing so doesn't make sense anymore.

Whenever a render is triggered, React will try to be as efficient as possible by reusing as much of the existing DOM Tree as possible.

##### The Reconciler:Fiber
- **Fiber Tree**: Internal tree that has a "fiber" for each component instance and DOM element
- Fibers are **NOT** re-created on every render
- Work can be done **asynchronously**
	- Rendering process can be split into chunks, tasks can be prioritized, and work can be **paused**, **reused**, or **thrown away**
		- Enables **concurrent features** like suspense or transitions
		- Long renders **won't block** JS engine
---

**Fiber Tree** -> Internal tree that has a "fiber" for each component instance and DOM element

**Reconciler** -> Determines what changed in the UI by comparing the new React Element Tree with the old one.

**Fiber** -> The internal system React uses to track and schedule updates efficiently

![[Pasted image 20250314145550.png]]

During the initial render of the application, Fiber takes the entire React Element Tree, so the Virtual DOM, and based on, it builds yet another tree which is the Fiber tree. 

The Fiber Tree is a special internal tree where for each component instance and DOM element in the app, there is one so-called **Fiber**. 

Unlike React Elements in the Virtual DOM, Fibers are not recreated on every render. So the Fiber Tree is never destroyed. Instead, it's a mutable data structure and once it has been created during the initial render, it's simply mutated over and over again in future reconciliation steps. 
This makes Fibers the perfect place for keeping track of things like the current component state, props, side effects, list of used hooks and more. 
So the actual state and props of any component instance that we see on the screen are internally stored inside the corresponding Fiber in the Fiber Tree.

Each Fiber also contains queue of work to do like updating state, updating refs, running registered side effects, performing DOM updates and so on. This is why a Fiber is also defined as a unit of work.

In Fiber Tree instead of normal parent-child relationship, each first child has a link to its parent and all the other children then have a link the their previous sibling. This kind of structure is called a **linked list**.

We all know that both trees include not only React Elements or components, but also regular DOM elements, such as the `h3` and `button` elements in this example. 

So both trees really are a complete representation of the entire DOM structure, not just of React components.

One extremely important characteristic of Fiber Reconciler is that work can be performed **asynchronously**. this meas that the rendering process which is what the reconciler does, can be split into chunks, some tasks can be prioritized over others and work can be paused, reused, or thrown away if not valid anymore.

There are, however, also some practical uses of this asynchronous rendering because it enables modern so-called **Concurrent Features** like suspense or transitions. It also allows the rendering process to pause and resume later so that it won't block the browser's JavaScript engine with two long renders, which can be problematic for performance in large applications. this is only possible because the render phase does not produce any visible output to the DOM yet. 

##### Reconciliation In Action (Reconciliation Process)
- 
---

![[Pasted image 20250314151948.png]]

So in the app component, there is a piece of state `showModal`, which is currently set to `true`. So let's say now that the state is updated to `false`. This will then trigger a re-render which will create a new Virtual DOM. and in this tree, the modal and all its children are actually gone because they are no longer displayed when `showModal` is not `true`. Also, all remaining React elements are yellow, meaning that all of them were re-rendered. It is because all children of a re-rendered element are re-rendered as well.

State update in `App` so **all remaining children** are re-rendered.

This new virtual DOM now needs to be reconciled with the current Fiber Tree, which will then result in this updated tree which internally is called the **Work In Progress Tree**. 

So whenever the reconciliation needs to happen, Fiber walks through the entire tree step by step and analyzes exactly what needs to change between the Current Fiber Tree and the Updated Fiber Tree based on the new Virtual DOM. and this process of comparing elements step by step based on their position in the tree is called **Diffing**.

**Diffing** -> Comparing elements step-by-step, based on their **position in the tree**.

So first, the `Btn` component has come new text and so the work that will need to be done in this Fiber is a **DOM update**. So in this case, swapping text from "Hide" to "Rate". Then we have the `Modal`, `Overlay`, `h3` and `Button`. So these were in the Current Fiber Tree but are no longer in the Virtual DOM and therefore they are marked as **DOM deletions**. Finally, we have the interesting case of the `Video` component. So this component was re-rendered because it's a child of the `App` component, but it actually didn't change. and so as a result of reconciliation, the DOM will not be updated in this case. 

Once this process is over, all these DOM mutations will be placed into a list called the **List Of Effects** which will be used in the next phase, so in a commit phase, to actually mutate the DOM.

**List Of Effects** -> Result of the Render Phase.

So the result of the reconciliation process is a second updated Fiber Tree, plus basically a list of DOM updates that need to be performed in the next phase. So React still hasn't written anything to the DOM yet, but it has figured out this so-called **List Of Effects** (Result of the Render Phase) so this is the final result of the render phase as it includes the DOM operations that will finally be made in the commit phase.

###### How Diffing Works
- 
---

**Diffing** -> Diffing is comparing elements step-by-step between two renders based on their position in the tree.

Diffing is based on two fundamental assumptions:
1. Two elements of different types will **produce different trees**
2. Elements with a stable key prop **stay the same across renders**

This allows the algorithm to be orders of magnitude faster going, from example, from a billion operations per thousand processed elements to just a thousand operations. 

There are basically two different situations that need to be considered. First, having two different elements at the same position in the tree between two renders. and second having the same element at the same position in the tree.
1. Same position, **Different** element
2. Same position, **Same** element 

**First Situation**:
![[Pasted image 20250316152109.png]]

Let's say that at some point an application is re-rendered, and in the diffing process, we find that an element has changed in a certain position of the tree. 

In a case of a DOM element changing like this, changing simply means that the type of the element has changed. Like in this example form a `div` to a `header`. 
So in a situation like this, React will assume that the element itself plus all its children are no longer valid. Therefore, all these elements will actually be destroyed and removed from the DOM. and that also includes their state, which is really important to remember. 

So as we see in this example, both the diff element and the `SearchBar` component will be removed from the DOM and will then be rebuilt as a `header` with a brand new `searchBar` component instance as the child. 
So if the child elements stayed the same across renders, the tree will actually get rebuilt, but it gets rebuilt with brand new elements. and so if there were any components with state, that state will not be recovered. So this effectively resets state.

Everything we have just said works exact same way for React Elements, So basically for component instances.
So here the `SearchBar` component changed to a `ProfileMenu` component and therefore the `SearchBar` is again completely destroyed including its state and removed from the DOM.

**Second Situation**:
![[Pasted image 20250316152626.png]]

The second situation is when between two renders we have the exact same element at the same position in the tree.
So if after a render, an element at a certain position in the tree is the same as before, the element will simply be kept in the DOM. and that includes all the child elements and more importantly, the components state. 

Same element at the same position in the tree stays the same and preserves state, and it works like this for DOM elements and for React Elements as well.

In this example we can actually see that something has changed. However, it was not the element type that has changed but simply the `className` attribute in the `div` and the `wait` prop in the `SearchBar` component. 

And so what React is going to do is to simply mutate the DOM element attributes. and in the case of React Elements it'll pass in the new props, but that's it. 

So React tries to be as efficient as possible and so the DOM elements themselves will stay the same. they're not removed from the DOM, and even more importantly the state will not be destroyed.

Nos sometimes we actually don't want this standard behavior but instead to create a brand new component instance with new state. and so that's where the `key` prop comes into play. 

#### Commit Phase
- **React Writes To The DOM**: Insertions, deletions, and updates (List of DOM updates are "flushed" to the DOM)
- **Committing is Synchronous**: DOM is updated is one go, it can't be interrupted. This is necessary so that the DOM never shows partial results, ensuring a consistent UI (in sync with state at all times)
- After the commit phase completes, the **Work In Progress** Fiber Tree becomes the **Current** tree **for the next render cycle**
---

**Commit Phase** -> Once React knows how to update a DOM, it does so in the commit phase. So in this phase, new elements might be placed in the DOM and already existing elements might get updated or deleted in order to correctly reflect the current state of the application. So it's really this commit phase that is responsible for what we traditionally call rendering, not the render phase.

The commit phase is where React finally writes to the DOM, so it inserts, deletes, and updates DOM elements. So basically, React goes through the Effects List that was created during rendering, and applies them one by one to the actual DOM elements that were in the already existing DOM tree. Now writing to the DOM happens all in one go. So we say that the commit phase is synchronous unlike the rendering phase, which can be paused. So committing can can not be interrupted. This is necessary so that the DOM never shows partial results which ensures that the UI always stays consistent.

Once the commit phase is completed, the work in progress fiber tree becomes the current tree for the next render cycle. That's because fiber trees are never discarded and never re-created from scratch. Instead, they are reused in order to save precious rendering time.

The browser will then notice that the DOM has been changed and as a result it will repaint the screen whenever it has some idle time. So this is where these DOM updates are finally made visible to the user in the form of an updated user interface. Browser Paint phase is performed by whatever browser the user is using. and the render phase is obviously preformed by the React library.

It is actually a separate library that writes to the DOM, and it's called the React DOM. 

React itself does never touch the DOM. So React only does the Render Phase but not the commit phase. The Reason for that is that React itself was designed to be used independently from the platform where elements will actually be shown, and therefore React can be used with many different so-called "hosts".

**Renderer** -> **Renderers** do not render, but they commit the results of the render phase.

The results of the Render Phase is not really a list of DOM updates, but a list of updates of whatever elements are used in the host that's being used. 

React library is not the one responsible for writing to the DOM. because the DOM is just one of many hosts to which React apps can be committed, so to which they can be output, basically. and each for these hosts we have a different package that we can use.

#### Browser Paint
**Browser Paint** -> Then finally, the browser will notice that the DOM has been updated and so it repaints the screen. This is the final step that actually produces the visual change that users see on their screens.

### Summary
So the whole process of rendering and displaying a React App on the screen, starts with a **trigger**, which can either be initial render of the app or, a state update in one of the components instances. 

This then triggers the render phase which does not produce any visual output, so this phase starts by rendering all component instances that need a re-render. and rendering in React simply means to call the component functions. this will create one or more updated React Elements which will be placed in a new Virtual DOM which is actually simply a tree of React Elements.

Rendering a component will cause all of its child components to be rendered as well, no matter if props changed or not. this is because React doesn't know whether children have been affected by the parent re-rendering or not.

This new virtual DOM needs to be reconciled with the current fiber tree, so with the representation of the element tree before the state update. this is necessary because it would be slow and inefficient to destroy and rebuild the entire DOM tree each time that something on the screen must be updated. Instead, reconciliation tries to reuse as much of the DOM as possible by finding the smallest number of DOM updates that reflect the latest state update on the screen.

This reconciliation process is done using a Reconciler called Fiber, which works with immutable data structure called the fiber tree. and in this tree, for each React Element and DOM element, there is a fiber, and this fiber holds the actual component state, props, and a queue of work.

After reconciliation, this queue of work will contain the DOM updates that are needed for that element. Now the computation of these DOM updates is performed by a diffing algorithm, which step by step compares the elements in the new virtual DOM with the elements in the current fiber tree, so to see what has changed. 

So final result of the render phase, so basically of this reconciliation and diffing process, is a second updated fiber tree as well as a list of all necessary DOM updates.

It is important to note that the render phase is asynchronous, So fiber can prioritize and split work into chunks and pause and resume some work later. and this is necessary for concurrent features and also to prevent the JavaScript engine to be blocked by complex render processes.

The output of the render phase, so the list of DOM updates will finally actually be written to the DOM in the commit phase. So in this phase, a so-called renderer like React DOM will insert, delete, and update DOM elements so that we end up with an updated DOM that reflects the new state of the application. and unlike the render phase, the commit phase is actually synchronous. So all the DOM updates are performed in one go in order to ensure a consistent UI over time.

Now finally, once the browser realizes that the DOM has been updated, it starts a new browser paint in order to visually update the user interface on the screen.

## The `key` prop
- Special prop that we use to tell the diffing algorithm that an element is **unique**
- Allows React to **distinguish** between multiple instances of the same component type
- When a key **stays the same across renders**, the element will be kept in the DOM (even if the position in the tree changes)
	- **Using keys in lists**
- When a key **changes between renders**, the element will be destroyed and a new one will be created (even if the position in the tree is the same as before)
	- **Using keys to reset state**
---

**`key` prop** -> Special prop that we can use to tell the diffing algorithm that a certain element is unique.

this works for both DOM elements and React Elements.

So in practice, this means that we can give each component instance a unique identification, which will allow React to distinguish between multiple instances of the same component type.

Whenever an element has a stable key, so a key that stays the same across renders, the element will be kept in the DOM, even if the position in the tree has changed. and this is the whole reason why we should use this `key` prop in lists. 

On the other hand, when the key of a certain element changes between renders, the element will be destroyed and a new one will be created in its place, even if the elements position in the tree is exactly the same as before. 

And so this is great to reset state, which is the second big use case of the `key` prop.

### 1. Keys in Lists (Stable Key)
**No Keys**:
![[Pasted image 20250316160910.png]]

Same elements, but **different position in tree**, so they are removed and recreated in the DOM (bad for performance).

So we have a list with two `Question` items, which clearly have no `key` prop. When we add a new item to the list, the two list items that we already had are clearly still the same, but they will now appear at different positions in the React Elementary. 
They are no longer the first and second children but now they are the second and the third children. 

So, we basically have the same elements but at different positions in the tree. and so according to the differing rules, these two DOM elements will be removed from the DOM and then immediately recreated at their new positions. and this is obviously bad for performance because removing and rebuilding the same DOM element is just wasted work. But thing is that React doesn't know that this is a wasted work.

**With Keys**:
![[Pasted image 20250316161459.png]]

**Different Position in the tree**, but the key **stays the same**, so the elements will be kept in the DOM.

Key allows us to uniquely identify an element. 

So we can give React that information that it doesn't have on its own. and so now when we add a new item to the top of the list, the two original elements are of course, still in different positions of the tree but they do have a stable key. So, a key that stays the same across renders. 

So according to diffing rules, these two elements will now be kept in the DOM, even though their position in the tree is different. So they will not be destroyed. and the result will be a bit more of a performant UI.

### 2. Key Prop to Reset State (Changing Key)
- If we have the same element at the same position in the tree, the **DOM element and state** will be kept
---

![[Pasted image 20250316183504.png]]

Changing key is used to reset state in component instances.

So let's say we have this `Question`, inside `QuesitonBox` and we pass in this object as a prop. Now the `Question` component instance has an answer state, which right now is set to "React allows us to build apps faster". But now, let's imagine that the question changes to something different. 

So, we still have the same element at the same position in the tree. All that changed was the `question` prop.

So basically, what we need is a way to reset this state. this is where the `key` prop comes into play once again. 

So now, we have a `key` of `q23` in this first question, which allows React to uniquely identify this component instance. Then when a new question appears, we can give it a different key. and so by doing this, we tell React that this should be a different component instance and therefore, it should create a brand new DOM element. 
and the result of doing this is that the state will be reset, which is exactly what we need in this situation in order to make this small app work in a logical way.

So whenever we find ourselves in a position where we need to reset state, we just have to make sure that we give the element a `key` and that the `key` changes across renders.

## Rules for Render Logic Pure Components
- 
---

This is important because React requires that components are **pure** when it comes to render logic in order for everything to work as expected.

### The TWO types of logic in React components
- 
---

There are two types of logic that we can write in React components:
1. **Render** Logic
2. **Event Handler** Functions

So while the render logic is Code that renders the component and describes how it is being displayed on the screen, event handlers contain Code that actually does things, So basically Code that make things happen in the application.

![[Pasted image 20250316220517.png]]

#### Render Logic
- Code that lives at the **top level** of the component function
- Participates in **describing** how the component view looks like
- Executed **every time** the component renders
---

**Render Logic** -> Basically, all the code that lives at the **top level** of the component functions, and that participates in describing how the view of a certain component instance should look like.

So in this code example, there is a lot of render logic. We have two lines of code which declares variables and assigns them values at a top level, and then also the `return` block where our component returns it's JSX. So these describe exactly how the component will be displayed on the screen.

However, if we look closely, we can identify yet another piece of render logic here, even though this code is actually inside a function. 

So as we can see in the return block, the Code there is actually calling this `createList` function. and therefore, that logic also participates in describing the component view. and so, it's also render logic.

So basically, render logic is all the Code that is executed as soon as the component is rendered. So each time that the function is called.

#### Event Handler Logic
- 
---

**Event Handler Logic** -> Basically, pieces of code that are executed as a consequence of the event that the handler is listening to.

So in our example we have a line of Code that essentially registered handle `handleNewAnswer` for the `change` event and therefore `handleNewAnswer` is our event handle function.

So while the render logic is Code that renders the component, event handlers contain Code that actually does things. So basically Code that make things happen in the application.

So, event handler contain things like state updates, HTTP requests, reading input fields, page navigation, and many more. So all things that basically change and manipulate the application in some way.

### Rules for Render Logic
- **Components must be pure when it comes to render logic**: given the same props (input), a component instance should always return the same JSX (output).
---

In practice this means that render logic is not allowed to produce any side effects. So in other words, the logic that runs at top level and is responsible for rendering the component should have no interaction with the outside world. This means that render logic is no allowed to perform network requests to create timers or to directly work with the DOM API. For example, listening to events using at event listener.

Render Logic must also not mutate objects or variables that are outside the scope of the component function. and this is actually the reason why we cannot mutate props. It's because doing so would cause a side effect, and side effects are not allowed.

Finally, we really cannot update state or refs in render logic. and updating state in render logic would actually create an infinite loop, which is why we can never do that. State updates are technically not side effects.

We should keep in mind that these side effects are only forbidden inside render logic. this means that we have other options for running our side effects. 
First of all, we saw in the example that event handler functions are not render logic and therefore, side effects are allowed and actually encouraged to be used inside these functions. 
And second, if we need to create a side effect as soon as the component function is first executed, we can register that side effect using a special hook called `useEffect`.

## How Events Work React
### DOM Refresher: Event Propagation and Delegation
- By default, event handlers listen to events on the target **and during the bubbling phase**
- We can **prevent bubbling** with `e.stopPropagation()`
- **Event Delegation**:
	- Handling events for multiple elements centrally in **one single parent element**
	- Better for performance and memory, as it needs only **one handler function**
---

![[Pasted image 20250321205556.png]]

So let's consider this tree of DOM elements, and this really is a DOM tree, So not a fiber tree or a React Element Tree.

Now let's say that some event happens, like a click on one of the three buttons, and so here is what's gonna happen in the browser.

As soon as the event fires, a new event object will be created, but it will not be created where the click actually happened. Instead, the object will be created at the root of the document, so at the very top of the tree. From there, the event will then travel down the entire tree during the so-called **Capturing Phase**, all the way, until it reaches the **Target Element**, and the target element is simply the element on which the event was actually first triggered.

So at the target, we can choose to handle the event by placing an event handler function on that element, which usually is exactly what we do. Then immediately after the target element has been reached, the event object travels all the way back up the entire tree during the so-called **Bubbling Phase**.

There are two very important things to understand about this process:
- The first is that during capturing and bubbling phase, the event goes through every single child and parent element one by one. In fact, it's if the event originated or happened in each of these DOM elements. 
- The second important thing is that by default, event handlers listen to events not only on the target element, but also during the bubbling phase.

so if we put these two things together, it meant that every single event handler in a parent element will also be executed during the bubbling phase as long as it's also listening for the same type of event. 
For example, if we added another click event handler to the header element, then during this whole process both the handlers at the target and the header element would be executed when the click happens. 

Sometimes we actually don't want this behavior, and so in that case, we can prevent the event from bubbling up any further simply by calling the `stopPropagation` method on the event object. and this works in Vanilla JavaScript, and also in React, but it's actually very rarely necessary, so we only use this if there really is no other solution.

The fact that events bubble like this allows developers to implement a very common and very useful technique called **Event Delegation**.

So with event delegation, we can handle events for multiple element in one central place, which is one of the parent elements. 

So we can imagine that instead of three buttons, there would be like, 1000 buttons. If we wanted to handle events on all of them, each button would have to have its own copy of the event handler function, which could become problematic for the app's performance and memory usage. 

So Instead, by using event delegation, we can simply add just one handler function to the first parent element of these buttons. Then when a click happens on one of the buttons, the event will bubble up to the options `div` in this example where we can then use the events target property in order to check whether the event originated from one of the buttons or not, and if it did, we can then handle the event in this central event handler function. 

This is what React does to our events behind the scenes.

### How React Handles Events
- React Registers all event handlers on the **root DOM container**. This is where **all events are handled**
- Behind the scenes, React performs **event delegation** for all events in our application
---

![[Pasted image 20250322094340.png]]

So let's consider this same DOM tree, and let's say again that we want to attach an event handler to one of the buttons, or even to some other DOM element. and this is what that would look like in React Code.

```jsx
<button 
	className="btn"
	onClick={() => setLoading(true)}
/>
```

So we would simply use the `onClick` prop to listen for click events, and then pass it a function. 

When we think about how React actually registers these event handlers behind the scenes, we might believe that it would look something like this.

What Appears to be Happening:
```js
document
	.querySelector(".btn")
	.addEventListener(
		"click", 
		() => setLoading(true))
	);
```

So React might select a button, and then add the event handler to that element, that sounds pretty logical, However, _**This is actually not what React does internally**_.

What Actually Happens Internally:
```jsx
document
	.querySelector("#root")
	.addEventListener(
		"click", 
		() => setLoading(true))
	);
```

Instead, what React actually does is to register this and all other event handler functions to the `root` DOM container and that `root` container is simply the DOM element in which the React app is displayed. 

So, instead of selecting the button where we actually placed our event handler, we can imagine that React selects the `root` element, and then adds all our event handlers to that element, and we say imagine, because the way React does all this behind the scenes is actually a lot more complex than this.

Only thing that is worth knowing is that React **Physically Registers one event handler function per event type**, and it does so at the `root` note of the **Fiber Tree** during the render phase.

So if we have multiple `onClick` handlers in our Code, React will actually somehow bundle them all together and just add one big `onClick` handler to the `root` node of the fiber tree, and so this is yet another important function of the fiber tree.
What this means is that behind the scenes, React actually performs **Event Delegation** for all events in our applications. So we can say that React delegates all events to the `root` DOM container, because that's where they will actually get handled, not in the place where we thought we registered them, and so this works exactly how we just learned.

Whenever a click happens on the button, a new event object is fired off, which will then travel down the DOM tree until it reaches the target element. From there, the event will bubble back up. then as soon as the event reaches the `root` container where React registered all our handlers, the event will actually finally get handled according to whatever handlers match the event and the target element. Finally, once that's all done, the event, of course, continues bubbling up until it disappears into nowhere.

We should notice that it is the DOM tree that matters and not the component tree. So just because one component is a child of another component, that doesn't mean that the same is true in the displayed DOM tree.

### Synthetic Events
- **Synthetic Event**: Wrapper around the DOM's native event object
- Has **same interace** as native event objects, like `stopPropagation()` and `preventDefault()`
- Fixes browser inconsistencies, so that events work in the exact **same way in all browsers**
- **Most synthetic events bubble** (including focus, blur, and change), except for scroll
---

![[Pasted image 20250322103120.png]]

**Synthetic Events** -> basically a thin wrapper around the DOM's native event object, and by wrapper we simply mean that synthetic events are pretty similar to native event objects, but they just add or change some functionalities on top of them.

So these synthetic events have the same interface as native event objects, and that includes the important methods, `stopPropagation()` and `preventDefault()`. What's special about synthetic events though, and one of the reasons why the React team decided to implement them is the fact that they fix some browser inconsistencies, making it so that events work in the exact same way in all browsers. 

The React team also decided that all of the most important synthetic events actually bubble, including the `focus`, `blur`, and `change` events, which usually do not bubble. The only exception here is the `scroll` event.

So whenever we declare an event handler like this one, React gives us access to the event object that was created, just like in Vanilla JavaScript. However, in React, this event object is actually different. 

So in Vanilla JS, we simply get access to the Native DOM event object, for example `PointerEvent`, `MouseEvent`, `KeyboardEvent` and many others. React, on the other hand, will give us something called a **Synthetic Event**.

### Event Handlers in React VS. JS
- Attributes for event handlers are named using **camel Case** (`onClick` instead of `onclick` or `click`)
- Default behavior can **not** be prevented by returning `false` (only by using `preventDefault()`)
- Attach `Capture` if you need to handle during **capture phase** (example `onClickCapture`)

## Some Guidelines and Summary of Important Information Written Above. Practical Takeaways and Conclusions (Practical Summary)
- A **Component** is like a blueprint for a piece of UI that will eventually exist on the screen. When we "use" a component, React creates a **component instance**, which is like an actual physical manifestations of a component, containing props, state, and more. A component instance, when rendered, will return a **React Element**
- "Rendering" only means **calling component functions** and calculating what DOM elements need to be inserted, deleted, or updated. It has nothing to do with writing to the DOM. Therefore, **each time a component instance is rendered and re-rendered, the function is called again**
- Only the **initial app render** and **state updates** can cause a render, which happens for the **entire application**, not just one single component 
- When a component instance gets re-rendered, **all its children will get re-rendered as well**. This doesn't mean that all children will get updated in the DOM, thanks to reconciliation, which checks which elements have actually changed between two renders. But all this re-rendering can still have an impact on performance
- Diffing is how React decides which DOM elements need to be added or modified. If, between renders, a certain React element **stays at the same position in the element tree**, the corresponding DOM element and component state will stay the same. If the element **changed to a different position**, or if it's a **different element type**, the DOM element and state will be destroyed
- Giving elements a `key` prop allows React to distinguish between multiple component instances. **When a key stays the same across renders**, the element is kept in the DOM. This is why we need to use keys in lists. **When we change the key between renders**, the DOM element will be destroyed and rebuilt. We use this as a **trick to reset state** 
- **Never declare a new component inside another component**! Doing so will re-create the nested component every time the parent component re-renders. React will always see the nested component as **new**, and therefore **reset its state** each time the parent state is updated
- The logic that produces JSX output for a component instance ("render Logic") is **not allowed to produce any side effects**: no API calls, no timers, no object or variable mutations, no state updates. **Side effects are allowed in event handlers and `useEffect`**
- The DOM is updated in the commit phase, **but not by React, but by a "renderer" called `ReactDOM`**. That's why we always need to include both libraries in a React web app project. We can use other renderers to use React on different platforms, for example to build mobile or native apps
- Multiple state updates inside an event handler function are **batched**, so they happen all at once, **causing only one re-render**. This means we can **not access a state variable immediately after updating it**: state updates are **asynchronous**. Since React 18, batching also happens in timeouts, promises, and native event handlers
- When using events in event handlers, we get access to a **synthetic event object**, not the browser's native object, so that **events work the same way across all browsers**. The difference is that **most synthetic events bubble**, including focus, blur, and change, which do not bubble as native browser events. Only the scroll event does not bubble
- **React is a library, not a framework**. This means that you can assemble your application using your favorite third-party libraries. The downside is that we need to find and learn all these additional libraries. 

## Component (Instance) Lifecycle
- 
---

**Component (Instance) Lifecycle** -> Basically encompasses the different phases that a specific Component Instance can go through over time.


### Mount / Initial Render
- Component instance is rendered for the **first time**
- Fresh state and props are **created**
---

First phase in any component's lifecycle is that a component instance is **mounted**. Which is also called the Initial Render. So this is when the component is rendered for the very first time.

This is also when fresh state and props are created for the Component Instance. and therefore, we can use the analogy that the component is born in this phase. 

### Re-Render
- Optional
- Happens When:
	- **State** changes
	- **Props** change
	- **Parent** re-renders
	- **Context** changes
---

Once the component has been rendered and is on the screen, it can be re-rendered an unlimited number of times.

A component will also be re-rendered when the props that it receives change, whens its parent component re-renders, or when something called **context** changes.

The Re-Render phase is actually **optional**, so it doesn't always happen in all components. So some components are only **mounted** and then **unmounted** right away.

### Unmount
- Component instance is **destroyed** and **removed**
- State and props are **destroyed**
---

Finally, there comes a point in time, where a component instance is no longer needed. and so that's when the component instance is **Unmounted**.

this is when the component basically dies. 
So in this step the component instance is completely destroyed and removed from the screen along with its state and props. 

Of course, a new instance of the same component can be mounted later, but this specific instance is now gone. So it has been **unmounted**. 

## Effects
- Effects allow us to write Code that will run at **different moments**: mount, re-render, or unmount
- Thinking about synchronization, **not** life cycles
---

```jsx
useEffect(function () {
	fetch(`http://www.omdbapi.com/?s=inception`)
		.then(res => res.json())
		.then(data => setMovies(data.Search));

	return () => console.log("Cleanup");
}, []);
```

The exact moment at which the effect is executed actually depend on its dependency array. 

So we can basically use this dependency array to tell the effect to also run after a component re-renders. 

**Cleanup Function in Effect** -> Cleanup function is returned from effect function, which is a function that will be invoked after the component re-renders or unmounts.

This array is just one of three parts that any effect can have. So besides the dependency array we have the effect Code itself, and also each effect can return a so-called **cleanup** function, which is a function that will be called before the component re-renders or unmounts.

We should actually not think about life cycles, but about synchronization.

So the real reason why effects exist is not to run Code at different points of the life cycle, **but to keep a component synchronized with some external system**. 
While on the other hand we use event handlers to React to a certain event that happened in the UI.

Event Handlers are always the preferred way of creating side effects. So basically everything that can be handled inside event handlers should be handled there.

### Where to Create Side Effects
- **Side Effect**: A **Side Effect** is basically any "interaction between a React component and the world outside the component". We can also think of a side as "code that actually does something". Examples: Data Fetching, Setting up subscriptions, setting up timers, manually accessing the DOM, etc.
- We need side effects all the time. They make our applications do something. **Not** in render logic!
- Sometimes triggering handlers by events is **not enough** for the application's needs
---

**Side Effect** -> A **Side Effect** is basically any "interaction between a React component and the world outside the component". We can also think of a side as "code that actually does something". Examples: Data Fetching, Setting up subscriptions, setting up timers, manually accessing the DOM, etc.

What this means is that we actually need side effects all the time when we build React apps. Now, we already know that side effects should not happen during the component render, or in other words side effects should not be in render logic. Instead, we can create side effects in two different places in React. and the first one is inside event handlers.

In some situations, we need to write some Code that will be executed automatically as the component renders. and so this is when we can create a so-called effect by using the `useEffect` hook.

So by creating an effect we can basically write Code that will run at different moments of a component instance life cycle. So when the component mounts, when it re-renders, or even when it unmounts.

### Event Handlers VS. Effects
- Produce the same result, but at **different moments**
---

For Example fetching movie data is very clearly a side effect because it's clearly an interaction with the world outside the component. 

There are two different possibilities of when we might want to create a side effect:
   1. The first possibility is that we might want to fetch data only when a certain event happens. So in that case, we would just use an event handler function.
   2. Other possibility of when to fetch the data would be to do so immediately after the component mounts, so after it is first rendered. 

So we can say that these two pieces of Code below produce the exact same result. So they both fetch data about a movie but they do so at a different moments in time.
So the event handler executes when an event happens and the effect executes whenever the component first renders.

#### Event Handlers
```jsx
function handleClick() {
	fetch(`http://www.omdbapi.com/?s=inception`)
		.then(res => res.json())
		.then(data => setMovies(data.Search));
}
```

- Executes when the **corresponding event happens**

#### Effects (`useEffect`)
```jsx
useEffect(function () {
	fetch(`http://www.omdbapi.com/?s=inception`)
		.then(res => res.json())
		.then(data => setMovies(data.Search));

	return () => console.log("Cleanup");
}, []);
```

- Executed **after the component mounts** (initial render), and **after subsequent re-renders** (according to dependency array)
- Used to keep a component **synchronized with some external system** (in this example, with the API movie data)

### What's the `useEffect` Dependency Array
- Be default, effects run **after every render**. We can prevent that by passing a **dependency array**
- Without the dependency array, React doesn't know **when** to run the effect
- **Each time one of the dependencies changes, the effect will be executed again**
- Every **state variable** and **prop** used inside the effect **MUST** be included in the dependency array
---

By default an effect will run after each and every render. We can change this default behavior by passing a dependency array into the `useEffect` hook as a second argument.

Without this array, React doesn't know when to actually run the effect. But, if we do specify the effect dependencies by passing in the dependency array, the effect will be executed each time that one of the dependencies changes.

**Effect Dependencies** -> effect dependencies are state variables and props that are used inside the effect.
the rule is that each and every one of those state variables and props must be included in the dependency array.

So, the effect function depends on the variables to do its work, and therefore we need to tell React about them. Otherwise, if the variables change, React won't know about this change, and, therefore, it won't be able to re-execute the effect Code. and, this will then lead to a bug called **stale closure**.

### `useEffect` is a Synchronization Mechanism
- `useEffect` is like an **event listener** that is listening for one dependency to change. **Whenever a dependency changes, it will execute the effect again**
- Effects **react** to updates to state and props used inside the effect (the dependencies). So **effects are "reactive"** (like state updates re-rendering the UI)
---

We can think of the `useEffect` hook as an event listener that is listening for one or more dependencies to change. and, when one of the dependencies does change, `useEffect` will simply execute the effect again.

So whenever the variables change, React will execute the effect again. So, essentially, effects react to updates to state and props that are used inside the effect, because those are the effects dependencies. 

So, the state and props of our component are now in fact synchronized with an external system. So, the synchronization only works in one way.

`useEffect` truly is a synchronization mechanism, so a mechanism to synchronize effects with the state of the application.

### Synchronization and Life Cycle
- **Effects** and **component life cycle** are deeply connected
- We can use the dependency array to run effects **when the component renders or re-renders**
---

Whenever a dependency changes, the effect is executed again. dependencies are always state or props. 
Whenever the state or props change component will re-render, which means that effects and the life cycle of a component instance are deeply interconnected. 

We can use the dependency array in order to run effects whenever the component renders or re-renders. So, in a way, the `useEffect` hook is actually about synchronization and about the component life cycle.

There are 3 different types of dependency arrays that we can specify and also how they affect both synchronization and life cycle:
   1. `useEffect(fn, [x, y, z]);`
	   - Effect synchronizes with `x`, `y`, and `z`
	   - Runs on **mount** and **re-renders** triggered by updating `x`, `y`, or `z`
   2. `useEffect(fn, []);`
	   - Effect synchronizes with **no state/props**
	   - Runs only on **mount** (initial render)
   3. `useEffect(fn);`
	   - Effect synchronizes with **everything**
	   - Runt on **every render** (usually bad)


So, when we have multiple dependencies like in first example, variables `x`, `y`, and `z`, it means that the effect synchronized with `x`, `y`, and `z`. In terms of the life cycle, it means that the effect will run on the initial render and also on each re-render triggered by updating one of the dependencies `x`, `y`, or `z`. The effect will be executed each time the component instance is being re-rendered by an update to `x`, `y`, or `z`. But, if some other piece of state or prop is updated, then this particular effect will not be executed.

If we have an empty dependency array, that means that the effect synchronizes with no state or props, and therefore it will only run on mount. In other words, if an effect has no dependencies, it doesn't use any values that are relevant for rendering the component. and, so, therefore, it's safe to be executed only once.

If we have no dependency array at all, we already know that the effect will run on every render, which is usually a really bad idea and not what we want. If the effect runs on every render, that basically means that the effect synchronizes with everything. So, essentially every state and every prop in the component will be dependencies in this case.

### When are Effects Executed?
- If an effects sets state, an **additional render** will be required
--- 

![[Pasted image 20250330141310.png]]

![[Pasted image 20250330141433.png]]

So, let's look at a timeline of event that happen as components render and re-render. 

The whole process starts with mounting the component instance. after that, the result or rendering is committed to the DOM, and finally the DOM changes are painted onto the screen by the browser.

Well, effects are actually only executed after the browser has painted the component instance on the screen. So, not immediately after render. that's why we say that effects run asynchronously after the render has already been painted to the screen.

Effects may contain long-running processes, such as fetching data. In a situation like that, If React would execute the effect before the browser paints a new screen, it would block this entire process, and users would see an old version of the component for way too long.

One important consequence of the fact that effects don't run during render phase is that if an effect sets state, then a second additional render will be required to display the UI correctly.

If props or state change, causing a re-render, the component will re-render, and the DOM changes will be committed and painted to the screen again. If the variable is part of the effect's dependency array, the effect will also be executed again at this point. and this whole process can of course be repeated over and over again until the component instance finally unmounts and disappears from the screen.

In React, there's actually another type of effect called a **layout effect**. So, the only difference between regular effect and a layout effect is that the layout effect runs before the browser actually paints the new screen.

### Cleanup Function
- Function that we can **return from an effect** (optional)
- Runs on two different occasions:
	1. Before the effect is **executed again**
	2. After a component has **unmounted**
- Necessary whenever the side effect **keeps happening after the component has been re-rendered or unmounted**
- Each effect should do **only one thing**! Use **one `useEffect` hook for each side effect**. This makes effects easier to clean up.
---

**Cleanup Function** -> Cleanup function is a function that we can return from an effect, the cleanup function is optional.

![[Pasted image 20250330141433.png]]

The third part of an effect is the cleanup function.

How can we ensure that the page stays synchronized with the application, even after the component has disappeared? 

Basically what we need is a way to execute some Code as the component unmounts. We can do exactly that by returning a so-called **cleanup function** from the effect. 

The Cleanup function that we return from the effect is actually also executed on re-renders, so right before the next effect is executed again.

Cleanup function will run on two occasions:
   1. First, it runs before the effect is executed again, in order to cleanup the results of the previous side effect.
   2. It also runs right after the component instance has unmounted, in order to give us the opportunity to reset the side effect.


We have the dependency array, in order to run Code whenever the component mounts or re-renders. and now With a cleanup function, we also have a way to run some Code whenever the component unmounts. So with this we have the entire component life cycle covered.

Basically we need a cleanup function whenever the side effect keeps happening after the component has been re-rendered or unmounted. 
For example: if we start a timer we should stop it, or if we add an event listener, we should clean up by removing it. 

**Each effect should only do one thing**. So if we need to create multiple effects in our components, which is completely normal, just use multiple `useEffect` hooks. This no only makes each effect much easier to understand, but it also makes effects easier to clean up using a cleanup function.

## React Hooks and Their Rules
- Special built-in functions tat allow us to **"hook" into React internals:**
	- Creating and accessing **state** from Fiber tree
	- Registering **side effects** in Fiber tree
	- Manual **DOM selections**
	- Many more...
- Always start with "**use**" (`useState`, `useEffect`, etc.)
- Enable easy **reusing of non-visual logic**: we can compose multiple hooks into our own **custom hooks**
- Give **function components** the ability to own state and run side effects at different lifecycle points (before v16.8 only available in class **components**)
---

**React Hook** -> React hooks are essentially special functions that are built into React and which allow us to basically hook into some of React's internal mechanisms, or in other words, hooks are basically APIs that expose some internal React functionality.
such as creating and accessing state from the fiber tree, or registering side effects in the fiber tree.

Using `useState` or `useEffect` hook we can essentially hook into that internal mechanism. 

Hooks also allow us to manually select and store DOM notes, access context, and many, many other things. 

We can even create our own so-called **Custom Hooks**, which will also start with the word "use". Custom hooks give us developers an easy way of reusing non-visual logic. So logic that is no about the UI.

### Overview of All Built-In Hooks
React actually comes with almost 20 built-in hooks.

#### Most Used
So `useState` and `useEffect` are, of course, some of the most important hooks, and therefore the most used ones, along with `useReducer` and `useContext`.

- `useState`
- `useEffect`
- `useReducer`
- `useContext`

#### Less Used
- `useRef`
- `useCallback`
- `useMemo`
- `useTransition`
- `useLayoutEffect`
- `useDebugValue`
- `useImperativeHandle`
- `useId`

Here we have this huge list of some less used hooks, but where some of them are actually still quite important. Some of these are actually worth learning, but others are a bit more obscure.

#### Only For Libraries
- `useSyncExternalStore`
- `useInsertionEffect`

Finally, there are a few hooks that are intended only for library authors. 

### The Rules of Hooks
- 2 Rules we must follow:
	1. Only call hooks at the top level
		- Do **NOT** call hooks inside **conditionals**, **loops**, **nested functions**, or after an **early return**
		- This is necessary to ensure that hooks are always called in the **same order** (hooks rely on this)
	2. Only call hooks from React functions:
		- Only call hooks inside a **function component**  or a **custom hook**
---

There are two very simple rules of hooks that we must follow:
 1. Hooks can only be called at the top level.
 2. Hooks can only be called from React functions.

**First rule**: This means that we cannot call hooks inside conditionals, like `if` statements, and also not inside loops or functions nested inside the component. We can also not call hooks after an early return, because that's also similar to a condition.

Hooks only work if they are always called in the exact same order, which can only be ensured if we only call them at the top level. 

**Second Rule**: This means that hooks can only be called from function components or from custom hooks, but not from regular functions or even class components. 

These Rules are **automatically enforced** by React's ESLint Rules.

### Hooks Rely on Call Order
Whenever an application is rendered, React creates a tree of React elements, also called the Virtual DOM. On the Initial Render, React also builds a fiber tree out of the Virtual DOM, where each element is a fiber. 

Each of these fibers contains a lot of stuff, like the received props, a list of work, and crucially for us, a linked list of all the hooks that were used in the component instance.

![[Pasted image 20250408234521.png]]

Our List will be built based on the call order of the used hooks.

So first this `useState` call, then another `useState` call. and then finally this `useEffect` call. So this is our list of hooks, but it's not a linked list yet.

**Linked List** -> Linked means that the first list element contains a reference to the second element, which in turn, has a link to the third list element. So all the list elements are linked together, which is actually a common data structure in computer science.

Moving back to our Code example.

Let's now imagine that a re-render happened, because State A was updated from 23 to 7, but this now creates a huge problem. We can notice how State B was only created initially because the condition A equaled 23 was true. However, after this re-render, the condition is now false, which means that this `useState` hook would not be called. and so State B would the no longer exist in this linked list of hooks after the render.

Well, the problem is that the first hooks is still pointing to the original second hook, so to State B, but that link is now broken. So State A is now linking to a hook that no longer exists, and nothing is pointing to the `useEffect` hook Z, meaning that a linked list has been destroyed. 

It works this way because fibers are not recreated on every render. and so this list is also not recreated. 
So if one of the hooks just disappears from the list, then the order of the list will get completely broken. 

So in conclusion, if we conditionally use the hook, like we did here, that will completely mess up the list of hooks between renders, which will leave React confused and unable to correctly track all the hooks that were used.

This opens up the question of why even bother having this linked list, if it requires this strange rule to exist. 
Well, the big reason is that a linked list, which relies on the hook call order, is the simplest way to associate each hook with its value. So basically, the order in which the hook is called uniquely identifies the hook. 
For example, React knows that hook number one has a state of 23, and that hook number two has a state of empty string.

So the value is associated with the call order. and this is very convenient because by using the call order, we developers don't have to manually assign names to each hook, which would create multiple problems.

## `useState` Hook 
### Summary of Defining and Updating State
- 
---

So we use the `useState` hook to first create state and then the setter function that results from creating state to update state.

We can create a state variable in the simple way which is what we do most of the time
```jsx
const [count, setCount] = useState(23);
```

but we can also create state based on a callback function.
```jsx
const [count, setCount] = useState(() => localStorage.getItem("count")
);
```

So whenever the initial state depends on some computation for example, reading data from local storage, we can pass in a callback function like this instead of just a single value, and this process is sometimes called **lazy evaluation**.

This callback function is only called on the initial render of the component. So on subsequent re-renders it will simply be ignored. Also, this callback needs to fulfill two requirements. First, it must be a pure function, and second it should require no arguments in order to work.

We can update state in a simple way just by passing a single value into the returned setter function as the next state.
```jsx
setCount(1000);
```

So in this example the next state would be 1000.

On the other hand, in many situations we actually want to update state based on the current state. for example, increasing a counter by one. So if that's the case we can give the setter function a callback function like this, so a function that is pure and returns the next state based on the current state.
```jsx
setCount((c) => c + 1);
```

One important rule that we have to keep in mind about updating state is that we should never mutate objects or arrays. Instead, we must create a new object or a new array which incorporates the changes that we want to make and then pass new object into the setter function.

### Conclusion
So in conclusion, both for creating and for updating state we have both a simply way and a way that requires a callback function.


## `useRef` Hook
- 
---

So we use the `useRef` hook to create something called a **ref**.

### What are Refs?
- **REF**: "Box" (object) with a **mutable** `.current` property that is **persisted across renders** ("normal" variables are always reset)
- We can write to and read from the ref using `.current`
- Two big use cases:
	 1. Creating a variable that stays the same between renders (e.g. previous state, `setTimeout` id, etc.)
	 2. Selecting and Storing DOM elements
- Refs are for **data that is NOT rendered**: usually only appear in event handlers or effects, not in JSX (otherwise use state)
- Do **NOT** read write or read `.current` in render logic (like state)
---

**REF** -> Ref stands for reference, and essentially, It's like a box into which we can put any data that we want to be preserved between renders.

In technical terms, when we use `useRef`, React will give us an object with mutable current property, and we can then write any data into this current property and also read from it.

```jsx
const myRef = useRef(23);
myRef.current = 1000;
```

In this small example, the current property was first set to the initial value of 23, and we then changed it to 1000. 

So as we can see, this current property is actually mutable, so unlike everything else in React. But what's really special about refs is that they are **persisted across renders**, so their `.current` property value stays the same between multiple renders, so just like state.

This gives us two big use cases for refs:
 1. First, we can use refs to create variables that will stay the same between renders. Examples: Preserving the previous state, or storing the ID of a `setTimeout` function.
 2. Second, we can select and store DOM elements. 
 

Just like the ID of a `setTimeout`, a DOM element is also a piece of data that we want to store and preserve across renders. 

Refs are usually for data that is not rendered in the visual output of the component. So usually refs only appear in event handlers or effects, but not in the JSX. 

If we need data that participates in the visual output of the component, that's usually a good sign that we actually need state and not a ref.

Just like with state, we are not allowed to write or to read the `.current` property in render logic as that would create an undesirable side effect. Instead, we usually perform these mutations inside a `useEffect` hook.

### State VS. Refs
In a way, we can say that refs are like state but with less powers.

What they have in common is that they are both persisted across renders. So the component remembers these values even after re-rendering. The big difference is that updating state will actually cause the component to re-render, while updating refs does not.

So the big takeaway from this is that we use state when we want to store data that should re-render the component and refs for data that should only be remembered by the component over time, but never re-render it.

Going back to the examples of preserving previous state and storing the ID of a `setTimeout`, these are pieces of data that we want React to remember between renders, but we don't want them to re-render the UI whenever we update them, and so that's why we use refs for this kind of data.

State is immutable, but refs are not. Also state is updated **asynchronously**, which means that we cannot use the new state immediately after updating it; with refs, on the other hand, updates are **not asynchronous**, and so we can actually read a new current property immediately after updating it. Basically, just like any other regular JavaScript object.

## What are Custom Hooks. When to Create One
- Allow us to reuse **non-visual logic** in multiple component
- One custom hooks should have **one purpose**, to make it **reusable** and **portable** (even across multiple projects)
- **Rules of Hooks** apply to custom hooks too
- Unlike components, can receive and return **any relevant data** (usually `[]` or `{}`) 
- Function name needs to start with **use**
---
### Reusing Logic With Custom Hooks
Custom hooks are all about reusability. In React, we have basically two types of things that we can reuse.
 1. A Piece of UI.
 2. A Piece of Logic.

If we want to reuse a piece of UI, we already know that we use a component. On the other and, if we want to reuse logic in React, we first need to ask the question, "does the logic that I want to reuse have any hooks?" if not, all you need is a regular function, which can live either inside or outside of your component. However, if the logic does contain any React hook, we cannot just extract the logic into a regular function. Instead, what we need create is a **custom hook**.

Basically, custom hooks allow us to reuse stateful logic among multiple component and actually not only stateful logic but really any logic that contains one or more React hook. 

So we can say, that custom hooks allow us to reuse non-visual logic, which is more generic term.

Just like regular functions or components or effects, one hook should only have one purpose. So it should only do one specific, well-defined thing. So the idea is not to simply put all the hooks of a component into a custom hook and call it a day. 
The idea is to make custom hooks reusable and portable so that we can even use them in completely different projects.

Since custom hooks are made out of regular React hooks, the rules of hooks that we have learned about before, still apply to them as well.

```jsx
function useFetch(url) {
	const [data, setData] = useState([]);
	const [isLoading, setIsLoading] = useState(false);

	useEffect(function () {
		fetch(url)
			.then(res => res.json())
			.then(res => setData(res));
	}, []);

	return [data, isLoading];
}
```

So first, a custom hook is really just a JavaScript function, so it can receive and return any data that is relevant to this custom hook. In fact, it's very common to return an object or an array from a custom hook.

We can notice how this is different from components, which are also just regular JavaScript functions but which can only receive props and always have to return some JSX.

Difference between regular functions and custom hooks is that custom hooks need to use one or more React hooks. So this custom hook here, for example uses two `useStaet` and one `useEffect` hook to abstract a simple fetch functionality into this custom hook.

Finally, in order for us and React to recognize this function as an actual hook, the function name needs to start with the word **use**. Just like all the built-in React hooks. In this example, that's `useFetch`. This is really not optional. We need to give the function a name, starting with **use**. otherwise, it's gonna be just a regular function in the eyes of React.

## Function Components VS. Class Components
- ![[Pasted image 20250414211107.png]]
---

Function Components are the current way of creating components in React, as they were introduced into React in 2019. Class Components, on the other hand, have been around for a long time, So since 2015.

Now technically React has always had function components but without hooks. Function components were very limited and not really useful, because they couldn't even have their own state.

In order to create a function component, we just use any type of JavaScript function, no matter if a function declaration or an arrow function. 
With Class components as the name says, we have to create an ES6 class that extends the provided `React.Component` parent class.

So when we're using class components, we're actually using object-oriented programming principles like having to use `this` keyword to read incoming props and to define local component state, which can become a bit annoying over time.

With function components on the other hand, these things are much easier. So to read props, all we have to do is to use the received props object. and to define local state, we can use `useState` hook.

Probably the biggest difference between these two types of components is how they handle side effects and the component lifecycle. 
So in class components, we actually have special methods that were defined by React in order to run Code at different points of the life cycle. and so these are called life cycle methods.
Now, with function components, we now care a lot more about synchronization rather than the component life cycle. and we do so by using the `useEffect` hook.

Hooks in general are the big and the main difference between function and class components. Hooks just introduced a completely new way of thinking and of writing React applications.

Some smaller differences are in event handlers and in the way in which we return the JSX from our components.
So in function components, we simply handle events with functions that we define inside the component function body.
While in class components, we have to create a new class method for every single event handler.

Now as for the JSX, in function components we return our JSX from the function, while in class components, we need to return JSX from a special render method, which is yet another React specific thing.

So in general function components with hooks have a lot of advantages over class components. They are easier to build, because they require a lot less React specific boilerplate Code, and they produce much cleaner Code. and the main reason for this cleaner code is that `useEffect` hook combines all Code related to the life cycle in one single place. While in class components, that Code is usually spread across multiple lifecycle methods, which cam become quite confusing in large components.

One of the big reasons that hooks were introduced in the first place is that they make it much easier to share stateful logic simply by creating custom hooks.
Finally, in function components, we can get rid of the annoying and error-prone `this` keyword, which was especially hard to grasp for many beginners. The only advantage, that class components have is the fact that some people find it easier to understand the component life cycle because of life cycle methods with explicit names such as `componentDidMount` or `componentWillUnmount`.

## Reducers and `useReducer` Hook
### Why `useReducer`?
- When components have **a lot of state variables and state updates** spread across many event handlers **all over the component**
- When **multiple state updates** need to happen **at the same time** (as a reaction to the same event, like "starting a game")
- When updating one piece of state **depends on one or multiple other pieces of state**
---

As components and state updates become more complex, using `useState` to manage all state is, in certain situations, not enough. For example, some components have a lot of state variables and also a lot of state updates that are spread across multiple event handlers all over the component or maybe even multiple components.

It's also very common that multiple state updates need to happen at the same time so as a reaction to the same event. For example, when we want to start a game, we might have to set the score to zero, set an `isPlaying` status and start a timer. 

Finally, many times updating one piece of state depends on one or more other pieces of state.

### Managing State With `useReducer`
- An alternative way of setting state, ideal for **complex state** and **related pieces of state**
- Stores related pieces of state in a **state** object
- `useReducer` needs **reducer**: function containing **all logic to update state**. **Decouples state logic from component**
- **reducer**: Pure function (**no side effects**!) that takes current `state` and `action`, **and returns the next state**
- **action**: object that describes **how to update state**
- **dispatch**: function to trigger state updates, by **"sending" actions** from **event handlers** to the **reducer**
---

So first of all, `useReducer` is an alternative way of setting and managing state, which is ideal for complex state and for related pieces of state.

```js
const [state, dispatch] = useReducer(reducer, initialState);

function reducer(state, action) {
	switch (action.type) {
		case "dec":
			return state - 1;
		case "inc":
			return state + 1;
		case "setCount":
			return action.payload;
		default:
			throw new Error("Unknown")
	}
}
```

So we call `useReducer` with a reducer function and its initial state and it returns a state and a dispatch function. 

Starting from the beginning, when we use `useReducer`, we usually store related pieces of state in a state object that is returned from the `useReducer` hook. It could also be a primitive value but usually, we use objects.

`useReducer` needs something called a **reducer** function in order to work. So this function is where we place all the logic that will be responsible for updating the state and moving all state updating logic from event handlers into this one central place allows us to completely decouple state logic from the component itself which makes our component so much more cleaner and so much more readable.

So when we manage state with `useReducer`, it's ultimately this reducer function that will be updating the state object.

In practice, the reducer is simply a function that takes in the current state and an action, and based on those values, returns the next state, so the updated state. 

We should keep in mind that state is immutable in React. This means that the reducer is not allowed to mutate the state, and in fact, no side effects are allowed in the reducer at all. So a reducer must be a pure function that always returns a new state. based on the current state and received action.

**action** -> the action is simply an object that describes how state should be updated. it usually contains an action type and so-called payload which is basically input data.

It is based on this action type and payload that the reducer will then determine how exactly to create the next state.

**How do we actually trigger a state update**? That's where the **dispatch** function comes into play. 

So `useReducer` will return a so-called **dispatch** function which is a function that we can use to trigger state updates. We know use the **dispatch** function in order to send an **action** from the event handler where we're calling dispatch to the reducer. The reducer will then use this action to compute the next state.

### How Reducers Update State
- ![[Pasted image 20250418194100.png]]
---

So let's say that we're in an event handler in some component and we now need to update some state. We want to update state, what do we do?

```js
const [state, dispatch] = useReducer(reducer, initialState);

const action = {
	type: "updateDay",
	payload: 23
}

dispatch(action);
```

We call the dispatch function that we get back from `useReducer` in order to dispatch an action to the reducer. This action is an object that contains information for the reducer. So information about how the reducer should update the state.

In this case, the action type is `updateDay` and the payload is 23, which probably means that the reducer will set the day state to 23. 
The object doesn't need to have this exact shape with a type in the payload, but it's a standard that has been adopted by most developers.

Basically, the reducer takes in this action together with the current state and it will then return a brand new state object which we usually call the **next state** in the context of reducers. and as always with state, updating the state will then trigger a re-render of the component instance.

It is called a Reducer function because it follows the exact same idea as the `array.reduce` method. So just like the reduce method accumulates all array values into one single value, the React reducer accumulates all actions into one single state over time.

Behind the scenes, the dispatch function has access to the reducer because we passed it into the `useReducer` hook, So dispatch is really coordinating this whole thing and also giving the reducer access to the current state.

So when we use `useState`, we get back a setter function and let's just call it `setState`. and then when we want to update state, we just pass the new updated state value that we want and React will simply update the state which in turn will trigger the re-render. `useState` is simpler and more straightforward compared to the complicated logic of the `useReducer` hook, even though it is hard to set up and more complicated, it has a big advantage over `useState` in some certain situations.


### A Mental Model for Reducers
So we can imagine that we needed to take $5,000 out of our bank account for some reason. Now, since this is a large amount, you can't just do it from an ATM, so we need to go physically to a bank.

Once we are at the bank, how do we actually get those $5,000? Do we walk straight into the bank's vault, grab the cash, and then go home? Well, we don't think so, right? That's usually not how it works.
How it does work is that we go into the bank and then we'll find a person sitting at a desk ready to assist us. When we arrive at the bank, we already know how much cash we want to withdraw and from what account number. and so we walk right to the person and tell them that we would like to withdraw $5,000 from account 923577 for example.
What happens then is that usually the person will type something into his computer, check if you actually have the cash in your account, and if so, he goes to the bank's vault, and gets the money to finally hand it over to you. It's our money after all.

But we should note the big difference between this real version and the previous version of the story where we just grabbed the cash ourselves. 
In this real version, we told the person what to do and how to do it and he then got the money for you on your behalf, and so we didn't take the money directly ourselves. and that's a huge difference. 

and so let's now bring this analogy back to `useReducer` and identify what each of these pieces represents in the `useRedcuer` mechanism. 

Let's start with the most important thing, the state. Well, the **state** is represented by the bank's vault because this is where the relevant data, so the money is stored and also updated. So the vault is what needs to be updated, and so that's our state.

Let's think about how the money is taken from the vault. So about how state is actually updated. So starting from the beginning, the customer going to the bank and requesting the money is clearly the **dispatcher** because it is who is requesting the state update. and they're doing so by going to the person and requesting to withdraw the $5,000.
The reducer is going to be the person working at the bank because that's the one who actually makes the update. In this case, it's the one who goes to the vault to get your money. 
But how does the person know how much money to take and from what account? They know because we told him so exactly in our request message. and so that request message is clearly the **action**. In this example, the action can be modeled like this.

```js
const action = {
	type: "withdraw",
	payload: {
		amount: 5000,
		account: 923577,
	}
}
```

With the action type being withdraw and the payload being the data about the withdrawal that we want to make. 

So summarizing, we went into the bank with a clear **action** in mind, we then **dispatched** that action to the **reducer**, so the person working there who took the action, and followed the instructions to take the right amount of money from your account So from **state**. he then gave us our money finishing this **cycle**. 

So we did not go directly into the vault and took our money. Instead, we had the person, as a middleman, who knows a lot better then us how to perform different actions on the vault. So he knows, how to deposit, how to withdraw, how to open and close an account, how to request a loan, and more. and he does all this without you having to worry about the details. 
So exactly like a **reducer function**, which also **decouples** and **abstracts** all the state updating logic away from us, so that we can have clean and easy to understand components.

### `useState` VS. `useReducer`
- `useState`
	- Ideal for **single, independent pieces of state** (numbers, strings, single arrays, etc.)
	- Logic to update state is placed directly in event handlers or effects, **spread all over one or multiple components**
	- State is updated by **calling  `setState`** (setter returned from `useState`) 
	- **Imperative** state updates
	- **Easy** to understand and to use
- `useReducer`
	- Ideal for multiple **related pieces of state** and **complex state** (e.g. object with many values and nested objects or arrays)
	- Logic to update state lives in **one central place, decoupled from components**: the reducer
	- State is updated by **dispatching an action** to a reducer
	- **Declarative** state updates: complex state transitions are **mapped** to actions
	- More **difficult** to understand and implement
---

`useState` is ideal for single pieces of state that are independent from each other. So things like numbers, strings and also arrays or simple objects. 
On the other hand, we reach for `useReducer` when we have multiple pieces of state that are related and dependent on each other or when we have some really complex state on our hand.

When we have a few states with `useState`, the logic to update that state is usually placed right into event handlers or effects. and these might be spread all over the component or even located in child components if we're using lifted state.
That's where one of the big advantages of `useReducer` comes into play because with `useReducer` we centralize all state updating logic in one place which is the reducer function. and with this all that logic is nicely decoupled from the components. 

Then whenever we need to update the state we just dispatch an action to the reducer, which knows exactly how to perform state updates for different actions. So essentially reducers map state transitions to actions with well-defined names, which makes them a lot more declarative.

```js
// Using State to Update Data/State
setScore(0);
setPlaying(true);
setTimerSec(0);

// Using Dispatch/Reducer function from useRuducer to Update Data/State
dispatch({tyoe: "startGame"});
```

for example, instead of setting three separate states, like these in order to start a game, we can just dispatch the action `startGame`  and the reducer will then take care of the rest.

The only downside of this approach is that it can be a bit more difficult to understand and to implement. It can take a bit more  time, but that might be wort it. 

Now finishing our comparison here, with `useState`, of course we do not dispatch any actions. All we do is directly updating state by calling the `setState` function, which leaves us with state updates that feel a lot more imperative when compared to dispatching an action. But on the bright side, this of course is a lot easier to understand and to use because we don't have to write any reducer function. and most of the time this is completely fine.

### When to Use `useReducer`/Reducers?
- ![[Pasted image 20250421205912.png]]
---

So the first and most obvious question to ask ourselves is whether we only need one piece of state. If that's the case, then the answer is very simple. We just use one `useState` hook and call it a day.

If we do need more than just one piece of state the next question to ask is: do my states frequently need to be updated together? So just like in that game example from earlier. and if the answer is yes then we might have a good use case for a `useReducer`.
However, there's probably one more question that we need to ask first. are we willing to actually write a slightly more complex `useRedcuer` hook with a reducer function? and if we are not then we just keep using the `useState` hook. But if we are okay with taking the time to write a reducer then this is definitely a good use case for `useReducer`.

If our state does not update frequently together, then the next step is to figure out whether we need more than three or four pieces of related state and whether that state even includes some objects. So this is what we can call **complex state**. So in this case and if we're willing to actually write a reducer then `useReducer` is again the way to go.

Finally, our state might actually not be that complex but we still feel like we have way too many event handlers that make the component and also its child components too large and too confusing. In that case we might also consider going with `useReducer`. Otherwise, if the answer is no again, then `useState` is once again the way to go.

So in general, even after learning about `useReducer`, `useState` should probably still remain our default choice for managing React state. But if `useState` gives us one of these problems that we have been talking about above then it's time to consider a `useReducer`.

## Routing and Single-Page Applications (SPAs)
### What is Routing
- With Routing, we match **different URLs** to **different UI views** (React components): **routes**
- This enables users to **navigate between different applications screens,** using the browser URL
- Keeps the UI **in sync** with the current browser URL
- Allows us to build **Single-Page Applications**
---

![[Pasted image 20250422143706.png]]

**Routing** -> So when we use routing in web applications, we basically match different URLs to different views in the user interface. 

In the specific case of React, we match each URL to a specific React component, and we call each of these matches between a URL and a component a **route**. 
Then when one of those specific URLs gets visited, the corresponding React component will be rendered. So basically, this enables users to navigate between different screens of the application by simply using links and the URL in the browser.

At the same time, routing like this keeps the user interface nicely in sync with the current browser URL, which has a couple of nice advantages.

There are **Client-Side Routing** and **Server-Side Routing**, We now discussed Client-side Routing which only works this way on the client side, so in the user's browser. There is, of course, also routing on the server side, but not in client side React applications.

Most front-end frameworks have these client-side routing capabilities baked right into the framework. But React is different, because it relies on third party packages for many different functionalities, and routing is one of them. 

So in React, routing is usually handled by this third party package called **React Router**. Routing is fundamental for building something that we call single-page applications.

### Single-Page Applications (SPA)
- Application that is **executed entirely on the client** (browsers)
- **Routes**: different URLs correspond to different views (components)
- **JavaScript** (React) is used to update the page (DOM)
- **The page is never reloaded**
- Feels like a **native app**
- Additional data **might be loaded** from a web API
---

![[Pasted image 20250422145523.png]]

So single-page applications, or SPAs for short, are web applications that are executed entirely on the client, so only in the user's web browser. Single-page applications rely heavily on the concept of routes where different URLs correspond to different views.

Whenever a user clicks on a special link provided by the Router, the URL in the browser simply changes. In the case of React, this job is usually done by React Router. 
Changing the URL will then trigger the DOM to be updated as a result. and in single-page applications, it's always JavaScript that will update the DOM and therefore the page.

So usually on a normal web page, when we click on a line, the browser will load a completely new page and then show us that new page. But single-page applications are completely different. 
The page is simply updated by JavaScript, which means that there will never be a complete page reload. 
and that's the whole point of the single-page application. it's the entire app in just one page. So without any hard reloads. This makes the web application feel just like a native desktop or a mobile application, which is really a fantastic user experience.

Going back to React, whenever the URL is changed, React Router and React itself will update the DOM by simply rendering the component that corresponds to the new URL. and then, of course, the whole cycle can be repeated as many times as necessary. 

It quite common that some pages need to display some external data. Whenever that happens, a component can just load some additional data from a server, usually from some kind of web API. So while the single-page app itself runs entirely on the client, it can always communicate with a server in order to fetch some data that it needs. What we cannot do is to load a completely new page, because then it would no longer be a single-page app.

## Styling Options For React Applications
- 
---

So React really doesn't care about how we style our applications. and so as a result, we have a lot of different styling options, most of them being provided by third party libraries.

So the first option is to simply **apply some inline CSS** to JSX elements using the style prop. 
This is actually more common in React than in Regular HTML because of React's idea of separation of concerns. An inline style is scoped to the particular JSX element that it's applied to, which means that it is locally scoped, so it applies only to that exact element.

We can also include an **external CSS file**, and then simply apply the CSS classes using the `className` prop. and the same would actually also have worked for a SASS file. 
In this case, our styles are actually global, which means that every single JSX element in the entire application could use any of these classes in the external CSS file. and this can create huge problems, especially in big projects. So basically, global CSS is a nightmare in large apps.
So in professional projects, CSS is almost never global. Instead, CSS should be scoped to an individual component.

Next styling option is **CSS Modules**. CSS modules are pretty similar to regular CSS files with the difference that we write just one CSS file for each of our components. The styles in that file will then be scoped to only that component so that no other component can use them. and this then makes components way more modular and reusable. and at the same time, it better reflects React's separation of concerns.

If we want to take it even one step further, we can go with a **CSS in JavaScript Library** like styled components. So as the name says with CSS in JavaScript, we actually write our CSS inside a JavaScript file, so in the same file where we define our components. What's special about a CSS in JavaScript library is that it allows us to create React components that have our styles directly apply to them, which we can then use just like regular components. So this fully embraces the React philosophy that a component should contain all the information about its appearance, and so that includes CSS.

Finally, we can also use a **Utility-First CSS Framework** like Tailwind. So in Tailwind, we use predefined utility classes to define individual styles, to use `flexbox`, to make layouts responsive, to make hover effects, and really to design our entire UI, and all that without ever having to leave the JSX markup.

Finally, we do actually have one more option here, which is basically **to not write any CSS at all**. It is actually possible, because we can built our entire project using a fully fledged UI component library, for example, like Material UI, Chakra UI, or Mantine. So essentially, a component library like those contains all kinds of pre-built and pre-styled components that are common in most web applications. This is, however, not ideal for beginners.

## Storing State in the URL (Query String/ Query Parameters)
### The URL For State Management
- The URL is an excellent place to store UI state and an alternative to `useState` in some situations! **Examples**: open/closed panels, currently selected list item, list sorting order, applied list filters
- Easy way to store state in a **global place**, accessible to **all components** in the app
- Good way to **"pass" data** from one page into the next page
- Makes it possible to **bookmark and share** the page with the exact UI state it had at the time
---

The URL is actually also an excellent place to store a state and especially UI state. and with UI state, I mean state that affects what the UI looks like. So things like an open or closed panel. Or a currently applied list sorting order or filter. So these examples of state are great candidates to be stored in the URL and basically to be managed by the URL with React Router.

We might ask "Why would we want to do that?".

So the first reason is that placing state in the URL is an easy way to store state in a global place that is easily accessible to all components in the app. So before, if we wanted state to be accessible everywhere, we would have to store it in a parent component and then pass it all the way down to all child components using props. But if we place state in the URL, we can easily just read the value from there, wherever the component is in the component tree. So basically we can move some state management from React to the URL. 

Also, placing state in the URL is, in many situations, a good way to pass data from one page into the next page without having to store that data in some temporary place inside the app.

Finally, another amazing reason why we should place UI state right in the URL is that doing so makes it possible to bookmark or to share the page with the exact UI state that the page had at the time that we are sharing or bookmarking it. For example, in an online shop, we might be filtering products by color and by price. and if that filter is saved in the URL, we can then share the page with someone and they will see the exact same filters applied to the list of products.

```URL
www.example.com/app/cities/lisbon?lat=38.728&lng=-9.141

Path: /app/cities
Params/Parameters: /lisbon
Query String: lat=38.728&lng=-9.141
```

So in a URL like this, we already know that we have a path, for example, `app/cities`, and we can consider this part state because it corresponds to the component that is currently being displayed. But this part is not really useful for state management in the way we have been describing before.

So for actually storing state in the URL, we use **Path Params/Path Parameters** or the **Query String**. 
Now Params, which stands for parameters are very useful to pass data to the next page while the query string is useful to store some global state that should be accessible everywhere.

### Example: Params and Query String
- ![[Pasted image 20250425161632.png]]
---

```URL
www.example.com/app/cities/lisbon?lat=38.728&lng=-9.141

Path: /app/cities
Path Params/Path Parameters: /lisbon
Query String: lat=38.728&lng=-9.141
```

So this URL that we have just looked at corresponds to this view, and in the URL we see that the Param is Lisbon. and so because of that, the page that was loaded is exactly about the city of Lisbon. 

So by creating a link that points to a URL with this Param, we are able to pass the city name to the next page whenever the user click on that link. and of course, if the URL had another city name as the Param, let's say Berlin then the loaded page would be about Berlin.

```URL
www.example.com/app/cities/berlin?lat=52.536&lng=13.377

Path: /app/cities
Path Params/Path Parameters: /berlin
Query String: lat=52.536&lng=13.377
```

So in this example, we store `lat` and `lng` pieces of state in a query string which corresponds to disposition on the map. and the same is true, of course, for the other URL. So each of these cities has, of course, a unique location, and that location is reflected right in the URL. and so in this example, we leverage the power of the URL to manage state in an effective way by reading the city name and the GPS location from the URL instead  of using application state inside React.

## What is Context API
### A Solution To Prop Drilling
- ![[Pasted image 20250426183819.png]]
---

So let's say that in our application, we need to pass some state into multiple deeply nested child components just like in this fictional example.

So in this application, the components B and F both need access to the count state variable.
The first solution that comes to mind is to simply pass the state variable as props all the way down until it reaches the components that need the count state. However, this then creates a new problem, because passing props down through multiple levels of the tree can quickly become cumbersome and inconvenient.
So instead, what we need is actually a way of directly passing the state from a parent component into a deeply nested child component. So that would immediately solve the problem.

Well, it turns our that React has actually thought of that, and has given us the **Context API** to do just that. 

**Context API** -> So the **Context API** basically allows components everywhere in the tree to read state that a context shares.

### What is the Context API?
- System to pass data throughout the app **without manually passing props** down the tree
- Allows us to **"broadcast" global state** to the entire app
- **Provider**: gives all child components access to **value**
- **Value**: data that we want to make available (usually state and functions)
- **Consumers**: all components that read the provided context `value`
---

![[Pasted image 20250426184749.png]]

**Context API** -> So first of all, the Context API is a system to pass data throughout the application without having to manually pass props down the component tree. It essentially allows us to broadcast global state, so state that should be available to all the child components of a certain context.

**Provider** -> So the first part of the Context API is the **provider**, which is a special React component that gives all child components access to a so-called **value**. and this provider can sit everywhere in the component tree, but it's common to place it at the very top.

**Value** -> The **Value** is the data that we want to make available, so the data that we want to broadcast through the provider. and so we pass this value into the provider. Usually, this value contains one or more state variables and even some setter functions.

**Consumers** -> Finally, we have consumers, which are all the components that read the value that we passed into the provider. So in other words, consumers are the components that subscribe to the context, and so they're able to read the value from the context, and we can create as many consumers as we want for any context provider.

So whenever the context value is updated, all consumers will automatically be re-rendered, so all the component that are reading the context value. 
So, whenever the value that is shared is updated in some way, the provider will immediately notify the consumers about the value change, and it'll then re-render those components.

Now we know that an update to a context value also re-renders a component as long as that component is subscribed to that exact context.

We can create as many contexts as we want in our application and place them wherever we want in the component tree. and so all this allows us for new and interesting ways of managing state. 

## Thinking in React Advanced State Management
### Types Of State
- ![[Pasted image 20250427105913.png]]
---

So we can classify state in terms of **state accessibility** and in terms of **state domain**. 

#### State Accessibility
When it comes to state accessibility state can be either a **local state** or **global state**.

So Local State is only needed by one or a few components, while global state might be needed by many components in different positions of the tree. That's why local state is only accessible  inside the component that it was defined in plus maybe its child components while global state can actually be made accessible to every single component in the application. So it's the accessibility of a state variable that changes between local and global state.

If we need to create a new state variable in a component but we are not sure whether it should be local or global state, there is a very nice trick that can help. 
So all we need to do is to ask ourselves: "**if this component was rendered twice, should a state update in one of the components reflect in the other one?**" and if the answer is no, then it means  that it's local state. but if the answer is yes, we have found ourselves a global state variable.

#### State Domain
Moving on to the state domain, we can classify each piece of state as either **Remote State** or **UI State**.

So **Remote State** is basically all application data that is loaded from a remote server. So usually using an API. So it's basically state that lives on a server but that can be loaded into our application. 
**UI State** on the other hand is basically everything else. So things like the currently selected theme, applied list filters, form inputs, open panels and many, many more. So all state that is not the core application data that we usually fetch from an API is UI state.

So whenever we have some state, it's extremely important to always know whether we're dealing with remote stare or with UI state because they need to be managed in a completely different way.

So remote state is fundamentally different from UI state because we usually get it in an asynchronous way and because the data might need to be re-fetched and updated frequently. Therefore, in a large scale application, remote state should be cached, re-validated and so on. 
UI state on the other hand is usually synchronous and stored right in the application and does not interact with any servers at all. and so this means that UI state is very easy to handle with the things like `useState` or `useReducer`.

### State Placement Options
- ![[Pasted image 20250427142630.png]]
---

So, whenever we need a new piece of state, we have about six different options on where we can place it. 

If all we need is local state, then we simply place it in a **local components** using `useState`, `useReducer` or even `useRef`. 
Many times, we actually need a piece of state in multiple related components. and so then, it's time to lift the state up by placing it in a parent component of all the components that need it. So a **parent component** is another state placement option. 

However, even that sometimes is not enough. So sometimes we have actual global state and then one good solution is to place the state into a **Context**. So this is where Context API comes into play as we can use it together with `useState` or `useReducer` to manage global state. 

We should just note that context on its own is actually not who is managing the state. State still needs to be managed so to be created and updated by `useState` or by `useRedcuer`. But we then use the Context API to give all components in the tree access to that state. The Context API is actually best suited to manage UI state and not necessarily remote state. especially when we are building a bigger application.

So if we need to manage remote state in a complex application or just need a more efficient way of managing global state in general, we can opt for one of the many **third-party state management libraries** that exist in the React ecosystem. So we can place our global state into Redux, into React Query or SWR or Zustand or one of the many other external state management solutions. and some of these solutions are suited for global remote state and some for global UI state or both.

 Next up we got the **URL**. So the **URL** is yet another excellent place where we can store global state that we want to make easily shareable and bookmarkable or that we just want to pass between pages.

Finally, sometimes we need to store some data inside the **user's browser**. and in that case, we can use local storage, session storage or something like that. Now just like refs, this is state that won't actually re-render any components but it's still technically application state.

### State Management Tool Options
- ![[Pasted image 20250427143734.png]]
---

So if we combine all classifications of state according to accessibility and domain, we end up with these four combinations. So **Local UI State**, **Global UI State**, **Local Remote State** and finally, **Global Remote State**.

We simply manage **Local UI State** with the tools like `useState`, `useReducer` and `useRef`. 

When it comes to **Local Remote State**, we can use a simple fetch inside a `useEffect` in order to load data from a remote API and then store that data as state with `useState` or `useReducer`. However, this is usually only a good idea in small applications. In bigger applications, we usually just treat all remote state as global state.

So when we need to manage **Global Remote State** we have to choose if we want to use a general solution like the Context API or a library like Redux or if we want to use a tool that is highly specialized in managing remote state. So those are tools like React Query, SWR and RTK Query which have built-in mechanisms like caching and automatic re-fetching in order to deal with the asynchronous nature of remote state. 

Finally, **Global UI state**. And here, the Context API coupled with `useState` or `useReducer` is a great tool. If we need something a bit more performant, we can look into one of the third-party libraries. So something like Redux.

## Performance Optimization and Wasted Renders
### Performance Optimization Tools
- ![[Pasted image 20250502151545.png]]
---

So, there are three main areas that we can focus on when we need to optimize performance of React apps.
 1. First, we can try to prevent waster renders. 
 2. Second, we can improve the overall app speed and responsiveness.
 3. And third, we can reduce the bundle size.

So in order to prevent wasted renders, we can **memoize** components with `memo` or we can **memoize** objects and functions `useMemo` and `useCallback` hooks. We can also use a technique where we pass elements into other elements as children or as a normal prop in order to prevent them from being re-rendered.

To improve the perceived up speed, we can again use the `useMemo` and `useCallback` hooks and we can also use the modern `useTransition` hook net.

Finally, we can reducer the bundle size simply by **using fewer third-party packages** in our code base and we can also implement **code splitting** and **lazy loading**.

Also, we should keep in mind that this list  of tools and techniques, is by no means, exhaustive. So there are many other optimization best practices for example, not defining components inside other components.

### When Does a Components Instance Re-Render?
- A component instance only gets re-rendered in 3 different situations:
	1. State Changes
	2. Context Changes
	3. Parent Re-Renders
- **Remember**: A render does **not mean that the DOM actually gets updated**, it just means the component function gets called. But this can be an expensive operation.
- **Wasted Render**: A render that didn't produce change in the DOM
- Only a problem when they happen **too frequently** or when the **component is very slow**
---

To understand what wasted renders actually are, we first need to review when exactly a component instance gets re-rendered.

So in React, a component instance only gets re-rendered in three different situations.
 1. First, when the component state changes.
 2. Second, a component instance gets re-rendered whenever there's a change in a context that the component is subscribed to.
 3. Finally, whenever a component re-renders, all its child components will automatically be re-rendered as well. So third reason is a parent component re-rendering.

But now, we might be wondering what about prop changes? Doesn't updating props also re-render a component? Well, actually that's technically not the case. So, that's a common misconception.

But what actually happens is that props only change when the parent re-renders but when the parent re-renders, the children who receives the prop will re-render anyway. and so, the real reason why a component re-renders when props change is that the parent has re-rendered.

It's important to also remember that rendering a component does not mean that the DOM actually gets updated. So all that rendering means is that the component function gets called that React will create a new virtual DOM. and to all the diffing and reconciliation, which can be an expensive and wasteful operation.

**Wasted Render** -> So, a wasted render is basically a render that didn't produce any change in the DOM. So, it's a waste because all the diffing calculations still had to be done but it didn't result in any new DOM. and so therefore, all the calculations were for nothing. 

Most of the time, this is actually no problem at all because React is very fast. However, it can become a problem when re-renders happen way too frequently or when the component is very slow in rendering. and so, this can then make the application feel laggy and unresponsive. For example, not updating the UI fast enough after the user performs a certain action.

## Understanding Memo
### What is Memoization?
- **Memoization**: Optimization technique that executes a pure function once, and saves the result in memory. If we try to execute the function again with the **same arguments as before**, the previously saved result will be returned, **without executing the function again**.
- Memoize **components** with `memo`
- Memoize **objects** with `useMemo`
- Memoize **functions** with `useCallback`
- ![[Pasted image 20250502154611.png]]
---

Now the fundamental concept behind these three tools is memoization.

**Memoization** -> So memoization is an optimization technique that executes a pure function one time, so let's say function A and then it stores the results in memory, so in a **Cache**. Then if we later try to execute the same function again with the same inputs it will simply return the result that was previously stored in the cache. So the function will not be executed again. 

So if the arguments are exactly the same as before, it means that in a pure function, the output will be the same. therefore, it makes no sense to execute the entire Code again  if we can just read the cached result. on the other hand, if the inputs are different, then of course the function will simply be executed again. So that's the concept of memoization.

Well, in React we can use this technique to optimize our applications. So we can use the `memo` function to memoize components with exactly this principle, and we can use the `useMemo` and `useCallback` hooks to memoize objects and functions. and doing so will help us prevent wasted renders and improve the overall application speed.

### The `memo` function
- Used to create a component that will **not re-render when its parent re-renders,** as long as the **props stay the same between renders**
- **Only affects props!** A memoized component will still re-render when its **own state changes** or when a **context that it's subsribed to changes**
- Only makes sense when the component is **haevy** (slow rendering), **re-render often,** and does so **with the same props**
- ![[Pasted image 20250502160150.png]]
---

So React contains a `memo` function and we can use this function to create a component that will not re-render when its parent re-renders, as long as the passed props stay the same between renders. or in other words, we use `memo` to create a memoized component.

So the function inputs are props and calling a function mutliple times is equivalent to re-rendering in React. and therefore, memoizing a React component means to not re-render it, if props stay the same across renders. and just like with memoizing regular functions, this makes a lot of sense, because why re-render a component if the input data hasn't changed at all? 

The regular behavior in React without using `memo` is of course that whenever a component re-renders, the child component re-renders as well. on the other hand if we memoize the child component, it will not re-render as long as the props are the same as in the previous render. Now, of course, if the props do change, then the child component will need to re-render as well, in order to reflect this new data that it received.

It's super important to keep in mind that memoizing a component really only affects props. this means that a memoized component will still re-render whenever its own state changes or whenever there is a change in a context that a component is subscribed to. Because in these two situations, the component basically has new data that it needs to show in the UI, and so then it'll always re-render no matter if it's been memoized or not.

Does this means that we should go ahead and memo all our components? Well, the answer is no, not at all. So memo is only useful when we're dealing with a heavy component, so a component that creates a visible lag, or a delay when it's rendered. also, in order for memo to actually make sense, the component should render quite frequently and it should do so with the same props.

So first, if the props are usually different between re-renders, memo has no effect anyway and then there is absolutely no need to use it. and second, wasted renders are only a problem when the re-rendering happens too frequently or when the component is slow in rendering. therefore, if the component only re-renders from time to time of if the component is lightweight and fast anyway, then memoizing brings no benefit at all.

## Understanding `useMemo` and `useCallback`
### An Issue With memo
- ![[Pasted image 20250502161636.png]]
---

So we know in React whenever a component instance re-renders everything in there is recreated. So all values are always created again and that includes objects and functions that are defined within the component. So a new render gets new functions and new objects even if they are the exact same ones as before. 

We also know that in JavaScript two objects or functions that look the same, so that are exactly the same code are actually different unique objects. and the classing example here is that an empty object is different from another empty object.

Therefore, We can understand that if we pass a function or an object to a child component as a prop, that child component will always see them as new props whenever there is a re-render. and if props are different between re-renders then memo will simply not work, so it will not do its job. 

So in summary, if we memoize a component but then give it objects or function as props, the component will always re-render anyway because it'll always see these props as new props, even when they actually look exactly the same.

So solution for this problem is that, we can make objects and functions stable so we can actually preserve them between renders by memoizing them as well. and to do that, React gives us two more hooks. `useMemo` and `useCallbak`.

### Two New Hooks: `useMemo` and `useCallback`
- Used to memoize values (`useMemo`) and functions **(`useCallback`) between renders**
- Values passed into `useMemo` and `useCallback` will be stored in memory ("cached") and **returned in subsequent re-renders, as long as dependencies ("inputs") stay the same**
- `useMemo` and `useCallback` have a **dependency array** (like `useEffect`): whenever one **dependency array chages**, the value will be **re-created**
- ![[Pasted image 20250502164917.png]]
---

So we can use `useMemo` to memoize any value that we want to preserve between renders and `useCallback` to memoize functions between renders. and we will just use the word values for everything here because `useCallback` is actually just a special case of `useMemo`.

So whatever value that we pass into `useMemo` or `useCallback` will basically be stored in memory and that **cached** value will then be returned in future re-renders. So it will be preserved across renders as long as the inputs stay the same. 

In the case of `useMemo` and `useCallback` these inputs are called **dependencies**. So just like `useEffect`, `useMemo` and `useCallback` also have a dependency array. and this is how it works. 

Whenever one of the dependencies change the value will no longer be returned from the cache but will instead be recreated. So this is very similar to the `memo` function where a component gets recreated whenever the props change. It' just a different thing that we're memoizing here and a different way of specifying the inputs. but the idea is the same.

So the regular behavior in React when we do not memoize a certain value is of course that a new value is created whenever the component re-renders. On the other hand, when we do memoize the value then no new value is created on re-render and the cached value is returned instead. and so like this, the value will stay exactly the same. So it will be stable across renders. However, this is only true if the dependencies that we specify in the dependency array don't change. If they do change, then a new value is actually created as if the memoization has never happened.

Well, if props are objects or functions, we need to memoize these props in order to prevent wasted renders. and this use case is probably the biggest use case for `useMemo` and `useCallback`. and it made very easy to understand why there is a need for these hooks. However, there are actually two additional use cases.

So the second use case is to avoid expensive recalculations on every render. For example, we might have a derived state that is calculated from an array of 100,000 items. Now, if our component re-renders all the time, then React needs to do this expensive calculation over and over again each time there is a render. and so to fix this, we can simply preserver the result of that calculation across renders using `useMemo`. and so then React doesn't have to calculate the same thing time and time again.

Finally, another use case is memoizing values that are used in the dependency array of other hooks, for example, in order to avoid infinite `useEffect` loops. 

Now, just like with the `memo` function it's important to not overuse these hooks. So we should probably only use them for one of these three use cases and not start memoizing every single object and function everywhere.

## Don't Optimize Prematurely!
- ![[Pasted image 20250502170311.png]]
---

### DO
- **Find performance bottlenecks using the Profiler and visual inspection (laggy UI)**
- Fix those real performance issues
- Memoize expensive re-renders
- Memoize expensive calculations
- Optimize context if it has many consumers and changes often
- Memoize context value + child components
- Implement code splitting + lazy loading for SPA routes

### DON'T
- Don't Optimize Prematurely!
- Don't optimize anything if there is nothing to optimize...
- Don't wrap all components into `memo()`
- Don't wrap all values in `useMemo()`
- Don't wrap all functions in `useCallback()`
- Don't optimize context if it's not slow and doesn't have many consumers

## `useEffect` Rules and Best Practices
### `useEffect` Dependency Array Rules
- Every **state variable, prop, and context value** used inside the effect **MUST** be included in the dependency array
- All **"reactive values"** must be included! That means any **function** or **variable** that reference **any other** reactive value
- Dependencies choose themselves: **NEVER** ignore the `exhaustive-deps` ESLint rule!
- Do **NOT** use **objects** or **arrays** as dependencies (objects are recreated on each render, and React sees new objects as **different**, `{} !== {}`)
- The **same rules** apply to the dependency arrays of other hooks: `useMemo` and `useCallback`
---

The first rule is that every single state variable and prop that's being used in the effect must be included in the dependency array. However, this rule is not 100% complete because of two things:
 1. First, any context value that a component is subscribed to must also be included in the dependency array.
 2. And Second, actually we must include all so-called **reactive values** in the dependency array as well.

![[Pasted image 20250502171210.png]]

**Reactive Value** -> A Reactive Value is any value that is either state, a prop, a context value, or any other value that itself references one of the reactive values. 

So examples are these two pieces of state, these two variables right there, so because they reference the duration state, and even the format duration function, because it references the reactive values, minutes and seconds. So basically all values that are somehow connected to state, props, or context are reactive values.

Going back to dependency array this means that every single reactive value must be included, which again, includes any functions or variables that reference any other reactive value. and the goal of this is to avoid so-called **stale closures** that would otherwise occur inside the effect function.

and this means that basically the dependencies choose themselves. Because if we need to include all reactive values in the list, there's not much to think about. Therefore, we should never, ever ignore `exhaustive-deps` ESLint rule about missing dependencies and ensuring that our dependency arrays are correct at all times.

The Final rule is that we should not use objects or arrays as dependencies, because when we do so, it seems to work just fine, but in reality, the effect will re-run on every single render. The reason for that is that React checks if dependencies have changed between renders by simply comparing them using the triple equality operator. However, objects in JavaScript will have a different reference each time they are recreated. and therefore, even if the content of an object stays the same after a render, React will still see the old and the new object as different and will therefore re-run the effect.

**All these rules work the exact same for other hooks that also have dependency arrays**, so `useMemo` and `useCallback`.

### Removing Unnecessary Dependencies
- ![[Pasted image 20250502174352.png]]
---

We must include all reactive values in the list of dependencies. React calls this not lying about dependencies. However, in certain situations, including every single dependency in the array, can actually cost the effect to run way too often and introduce problems. But, the solution is not to omit one or more dependencies because that would be lying to React. Instead, we can use one of the strategies that can make some of the dependencies unnecessary, and so then we can remove those unnecessary dependencies from the array.


#### **Removing Function Dependencies**
- Move function **into the effect**
- If we need the function in multiple places, **memoize it** (`useCallbacl`)
- If the function doesn't reference any reactive values, move it **out of the component**
--- 

So first off, when we're dealing with helper functions as dependencies, the easiest way to remove the dependency is to just move the function right into the effect. Because if the function is inside the effect, then it's no longer a dependency of the effect. However, if we can't do that, because we might need the same function in multiple places, we can try to memoize it with `useCallback`. Also, if the function is not a reactive value itself, so if it doesn't use any reactive values inside the Code, then we can just move it entirely out of the component because it's not really a dependency anyway. and so by doing this, the function then doesn't need to be recreated on every render. 

#### **Removing Object Dependencies**
- Instead of including the entire object, include **only the properties we need** (primitive values)
- If that doesn't work, use the same strategies as for functions (**moving** or **memoizing** object)
---

Next up, if we want to use an object as a dependency, we can try to not include the entire object, but only the properties that we actually need inside the effect. and we can do this as long as these properties are primitive values, like strings or numbers. However, if for some reason that doesn't work for our specific situation, we can try one of the strategies that we mentioned for functions as they are quite similar.

#### **Other Strategies**
- If we have **multiple related reactive values** as dependencies, try using a **redcuer** (`useReducer`)
- We don't need to include `setState` (from `useState`) and `dispatch` (from `useReducer`) in the dependencies, as **React guarantees them to be stable** across renders
---

Finally, we have two other strategies.

First, if we find ourselves in a situation where our dependency list includes multiple reactive values that are related to one another, we can try using a reducer with `useReducer`. So sometimes a reducer can really be like a secret weapon that makes all our dependency problems completely go away. 

Also, there is no need to include the `setState` function from `useState` or the `dispatch` function from `useReducer` in the dependency array list, because React guarantees that these are stable between renders.

### When to NOT use an Effect
- Effects should be used as a **last resort**, when no other solution makes sense. React calls them an "escape hatch" to step outside of React
---

Effects should actually only be used as a last resort when no other solution really makes sense. That's the reason why React calls effects an escape hatch to step outside of React.

#### **Three Cases Where Effects Are Overused**
- **Responding to a user event**. An event handler function should be used instead
- **Fetching data on component mount**. This is fine in small apps, but in real-world app, a library like React Query should be used
- **Synchronizing state changes with one another** (setting state based on another state variable). Try to use derived state and event handlers
---

The first one is to use an effect to respond to a user event like a click or a keystroke. A user event should whenever possible be handled with an event handler function and not with an effect, even if the handler does create a side effect.

Next, Fetching data from an API when the component first mounts is another overused application of `useEffect`. in fact, in smaller apps, this is completely fine, but in more real world application, its best to use a professional data fetching library like React Query.

Finally, effects are overused a lot to synchronize state changes with one another, which means to use `useEffect` to listen for a state change only to set another piece of state. and the problem with this is that it will create multiple re-renders. But generally speaking, instead of using an effect to set state based on another state, we should rely on derived state and event handlers.

## The Bundle and Code Splitting
- **Bundle**: JavaScript file containing the **entire application code**. Downloading the bundle will load **the entire app at once**, turning it into a SPA
- **Bundle Size**: Amount of JavaScript users have to download to start using the app. One of the most important things to be optimized, so that the bundle takes **less time to download**
- **Code Splitting**: Splitting bundle into multiple parts that can be **downloaded over time** ("lazy loading")
---

So whenever some user navigates to our application, they're basically visiting a website that is hosted on some server. So that's just how every single website and web application work. Once the user actually navigates to the app, the server will send back a huge JavaScript file to the client that is requesting it. and this file is the **bundle**.

**Bundle** -> So the bundle is simply a JavaScript file that contains the entire code of the application. 

and it is called a bundle because a tool like Vite or Webpack has bundled all our development files into one huge bundle which, again contains all the application code. This means that once the code has been downloaded, the entire React application is loaded at once, which essentially turns it into a single-page application that is running entirely on the client.

So whenever the URL changes in the app, the client just renders a new React component but without loading any new files from the server because all the JavaScript code is already there in the bundle. 

The bundle size is of course the amount of JavaScript code that every single user needs to download in order to start using the application. So if the bundle has, for example, 500 kbs, then all those bytes need to be downloaded before the app even starts working. and of course, the bigger the bundle, the longer it's gonna take to download which can become a huge problem. Therefore, bundle size is probably the most important thing that we need to optimize.

So we can just use a technique called **Code Splitting**. and code splitting basically takes the bundle and, as the name says, splits it into multiple parts. So instead of just having one huge JavaScript file, we will have multiple smaller files which can then be downloaded over time as they become necessary for the application. and this process of loading code sequentially is called **Lazy Loading**.

## Introduction to Redux
### What is Redux?
- 3rd-party library to manage **global state**
- **Standalone** library, but easy to integrate with React apps using `react-redux` library
- All global state is stored in one **globally accessible store**, which is easy to update using "**actions**" (like `useReducer`)
- It's conceptually similar to using the Context API + `useReducer`
- Two "versions": (1) Classic Redux, (2) Modern Redux Toolkit
---

**Redux** -> In a nutshell, Redux is a third-party library that we can use to manage global state in a web application. 

Redux is actually a complete standalone library that we could use with any framework or even vanilla JavaScript. However, Redux has always been tightly linked to React and they are actually quite easy to connect using the `react-redux` library.

The big idea behind Redux is that all the global state in our application can be stored inside this one globally accessible store which we can then update using actions. In fact, the mechanism behind Redux and `useReducer` is very similar. 

The idea of updating the state in React and in Redux is always the same. So in the case of Redux, as soon as we update the store all the React components that consume some data from the store will be re-rendered. So conceptually, if we think about this Redux is quite similar to combining the Context API with the `useReducer` hook.

So there are basically two versions of Redux, So two different ways of writing Redux applications, but which are totally compatible with each other:
 1. **Classic Redux**
 2. **Redux with Redux Toolkit**

### Do We Need To Learn Redux?
![[Pasted image 20250506182342.png]]

### Redux Use Cases
So the recommendation of many experts is to use a global state management library like Redux, only when we have lots of global UI state that we need to update frequently. and we should remember that UI state basically means state that is not fetched from a server that would be remote state. 

So UI state is simply data about the UI itself or data that doesn't need to be communicated to an API or so. and this distinction is really important because for global remote state we have many better options nowadays like React Query, SWR, or even a tool that is kind of included in modern Redux Toolkit, which is Redux Toolkit Query.

![[Pasted image 20250506182744.png]]

### The Mechanism of the `useReducer` Hook
![[Pasted image 20250508224424.png]]

So with `useReducer` when we want to update state from an event handler in a component we start by creating an action. This action is simply an object that usually contains a `type` and `payload`, which is information about how the state should be updated.

We then dispatch that action to a so-called reducer function, the reducer takes the action type and the payload, and together with the current state calculates the next state, so the new state value. and to finish as the state updates, of course, the component that originated the state transition will re-render.

### The Mechanism of Redux
![[Pasted image 20250508224351.png]]

So the first difference between `useReducer` and Redux is that in Redux we actually dispatch actions not simply to the reducer, but to the **store**.

**Store** -> the store is a centralized container where **all global state lives**. it's like the single source of truth of all global state across the entire application. The store is also where one or multiple reducers live. 

And just as a reminder each reducer must be a pure function that has the single task of calculating the next state based on the action that was dispatched to the store and the current state that's already in the store as well.

We could be wondering why there is multiple reducer in this store. well, it's because we should create one reducer per application feature or per data domain in order to keep things separated. For example, in a shopping app, we could have one reducer for the shopping cart, one for some user data, and one for the application color theme. 

Finally, any component that consumes the state that has been updated in the store will as always get re-rendered by React at least if we're assuming that reusing Redux together with a React app.

So in the real world when we use Redux we usually use functions called **action creators** in order to automate the process of writing actions. So basically, instead of always writing these action objects by hand, we create functions that do this automatically. This has the advantage to keep all actions in one central place which reduces bugs, because developers don't have to remember the exact action type strings.

We should just note that this is optional and not a feature of Redux. It's just how we build real world Redux apps. Then the rest of the process is of course what we just have explained above.

So in order to update global state with Redux, we start by calling an action creator in a component, and then dispatch the action that resulted from the action creator. 
This action will then reach the store where the right reducer will pick it up and update the state according to the instructions. 
This then triggers a re-render of the UI where the cycle finishes. and the big goal of all this is to make the state update logic separate from the rest of the application.

## Redux Middleware and Thunks
- ![[Pasted image 20250619204332.png]]
- ![[Pasted image 20250619204422.png]]
- ![[Pasted image 20250619204434.png]]
- ![[Pasted image 20250619204349.png]]
---

### What is Redux Middleware?
- A function that sits between dispatching the action and the store. Allows us to run code **after** dispatching but **before** reaching the reducer in the store.
---

So let's say that we wanted to make an asynchronous call to some API. So where could we actually do that in Redux? 

Well, we can definitely not make the API call inside a reducer because reducers need to be pure functions with no side effects. So by itself, a Redux store doesn't know anything about performing asynchronous logic like this. It only knows how to synchronously dispatch actions and update the state. Therefore, any asynchronous operations like API calls need to happen outside a reducer. 

So instead, should we maybe fetch the data inside the component and then dispatch an action to the store with that received data? Well, that is actually possible, but it's not an ideal solution and the reason for that is that we usually want to keep our components clean and free of data fetching and we also want our important data fetching login encapsulated somewhere, so all in one place and not have it spread all over the application. Therefore, fetching data inside components is not ideal.

But if not in the store and not in the components, then where do we perform asynchronous actions? Well, that's where **Middleware** comes into action.

**Redux Middleware** -> So in Redux, Middleware is basically a function that sits between the dispatching and the store. This means that a middleware allows developers to run some code after dispatching an action, but before that action reaches the reducer in the store.

So again, usually after we dispatch, the action immediately reaches the reducer and the state is updated. But with a middleware, we can do something with the action before that action actually gets into the reducer. And therefore, this is the perfect place for our asynchronous API call, as well as other operations, such as setting timers, logging to the console, or even pausing and canceling the action altogether. So in essence, Middleware is the go-to place for side effects in the Redux cycle.

We can write Middleware functions ourselves, but usually, we just use some third party package, and in the case of asynchronous operations, the most popular Middleware in Redux is called **Redux Thunk**.

So now that we have this Thunk Middleware in place, the action will no longer be immediately dispatched, but will first get into the middleware. So into the Thunk, in this case. Then we can start fetching some data inside the Thunk, but it could also be some other asynchronous operation.

Now, as soon as the data arrives, we place it into the actions payload and then we finally dispatch the action into the store, where the state will then immediately get updated. 

So basically, the Thunk allows Redux to wait before dispatching the fetch data into the store. Or in other words, we have used the Thunk in order to defer dispatching into the future. So to the point in which the data that we need has actually arrived.

## What is Redux Toolkit (RTK)?
- The **modern and preferred** way of writing Redux code
- An **opinionated** approach, forcing us to use Redux best practices
- 100% compatible with "classic" Redux, allowing us to **use them together**
- Allows us to write **a lot less code** to achieve the same result (less "boilerplate")
- Gives us 3 big things (but there are many more...):
	1. We can write code that **"mutates"** state inside reducers (will be converted to **immutable** logic behind the scenes by "Immer" library)
	2. Action creators are **automatically** created
	3. **Automatic** setup of thunk middleware and Devtools
---

Redux Toolkit is the modern way of writing Redux Code, and it's advised by the Redux team to now prefer Redux Toolkit over classic Redux. That's because Redux Toolkit is an opinionated approach that forces everyone to use best practices that the community has learned over the years. So, basically, Redux Toolkit took all these best practices and placed them into this new way of writing Redux. 

First, without learning the classic Redux fundamentals, it's very hard to understand Redux Toolkit because it is built on top of classic Redux, of course. And, second, both ways of writing Redux are 100% compatible with each other. So we can actually use classic Redux in one part of the app and Redux Toolkit in another part.

The biggest advantage is certainly that Redux Toolkit allows us to write a lot less code to achieve the exact same result as before. So we say that we need a lot less boilerplate code, which is basically code that only sets things up but doesn't really do anything meaningful. And so Redux Toolkit hides all that stuff, like setting up middleware and the developer tools. 

So out of the box Redux Toolkit gives us many things. But the three highlights are, first, it allows us to write code that actually mutates state inside reducers. Now behind the scenes a library called "Immer" will convert our code back to non-mutating. The code will look as if we were mutating the state object directly.

Redux Toolkit also automatically creates action creators from our reducers, and this can be quite helpful as, again, it helps us writing less code. It can, however, also create some additional work in some situations as we will experience in practice soon.

Finally, Redux Toolkit will also automatically set up Thunk Middleware and the developer tools so that we can focus on writing code that actually does something in the application.

## Redux VS. Context API
### Redux
#### Advantages
- Built Into React
- Easy to set up a **single context**

#### Disadvantages
- Additional state "slice" requires a new context **set up from scratch** ("provider hell" in `App.js`)
- **No** mechanism for async operations
- Performance optimizations is a **pain**
- Only React DevTools

### Context API + `useReducer`
#### Advantages
- Once set up, it's easy to create **additional state "slices"**
- Supports **middleware** for async operations
- Performance is optimized **out of the box**
- Excellent DevTools

#### Disadvantages
- Requires additional package (larger bundle size)
- More work to set up **initially**

### When to use Context API or Redux?
There is no right answer that fits every project. it all depends on the projects needs!

#### Context API + `useReducer`
- Use the Context API for global state management in **small** apps
- When you just need to share a value that **doesn't change often** (Color theme, preferred language, authenticated user, ...)
- When we need to solve a simple **prop drilling** problem
- When we need to manage state in a **local sub-tree** of the app

#### Redux
- Use Redux for global state management in **large** apps
- When you have lots of global UI state that needs to be **updated frequently** (because Redux is optimized for this) (Shopping cart, current tabs, complex filters or search, ...)
- When you have **complex state** with nested objects and arrays (because we can mutate state with Redux Toolkit)

## Application Planning
### How to Plan and Build a React Application
#### Small Applications
- ![[Pasted image 20250625183510.png]]
--- 

We can build a simple React project by breaking the desired user interface into components, then building a static version without state in the beginning and then after that we think about the state management plus the data flow. So this works quite well for small applications that only have like one page and only very little features, but in a real world application we actually need a bit of a more complete process .

#### Real World Applications
- Gather application **requirements and features**
- Divide the application into **pages**:
	- Think about the **overall** and **page-level** UI
	- Break the desired UI into **components**
	- Design and build a **static** version (no state yet)
- Divide the application into **feature categories**:
	- Think about **state management + data flow**
- Decide on what **libraries** to use (technology decisions)
---

So when we build a large and more real world application we need to start by gathering the application requirements and the features that the application needs and then based on those we can divide our application into multiple pages.

Next up, we need to divide the application and the application features into multiple feature categories, so basically we need to place all the features into a few categories, so that we can then build the application around those and so that we can organize or code any logical way.

Finally, we will also need to decide on which libraries we actually want to use. So we call this the technology decisions because this is basically where we decide exactly what tech stack we are going to use to implement our application.

So as we divide the application into pages for each of the pages, we can think about the overall entity page level user interface and so then comes the time where we can break the desired user interface into its components. For each of the pages we can now design and build a static version. 

We should think about state management and data flow and so that we do for each of the feature categories. So for each of these categories that we identified we will now need to think about what data it needs and where we can store that data and so that's basically what state management is all about.

## What is Tailwind CSS?
- "A utility-first CSS framework packed with utility classes like `flex`, `text-center`, and `rotate-90`, that can be composed to build any design, directly in your markup (HTML or JSX)"
- **Utility-first CSS approach**: writing tiny classes with one single purpose, and then combining them to build entire layouts
- In tailwind, **these classes are already written for us**. So we're not gonna write any new CSS, but instead use some of tailwind's hundreds of classes
--- 

**Tailwind CSS** -> Tailwind is a utility-first CSS framework packed with utility classes like `flex`, `text-center`, and `rotate-90`, among many many other classes that can be composed to build any design directly in our markup. So, right in our HTML or JSX.

Well, basically when we write utility-first CSS, we write lots and lots of tiny classes where each class has one single purpose, and we then combine these classes to build entire components and layouts.

So, basically in tailwind, all these tiny classes are already written for us, ready to be used. So, when we use tailwind for, or styling we're not gonna write any new CSS at all. Instead, we will leverage some of tailwind's hundreds of classes to design and build anything that we can imagine.

### The Good and Bad about Tailwind
#### The Good
- We don't need to think about class names
- No jumping between files to write markup and styles
- Immediately understand styling in any project that uses tailwind
- Tailwind is a design system: many design decisions have been taken for you, which makes UIs look better and more consistent
- Saves a lot of time, e.g. on responsive design
- Docs and VS Code integration are great

#### The Bad
- **Markup (HTML or JSX) looks very unreadable**, with lots of class names (you get used to it)
- We have to learn a lot of class names (but after a day of usage you know fundamentals)
- We need to install and set up tailwind on each new project
- You're giving up on "Vanilla CSS"

## What is Supabase?
- Service that allows developers to easily **create a  back-end with a Postgres database**
- Automatically creates a **database** and **API** so we can easily request and receive data from the server
- **NO** back-end development needed
- Perfect to get up and running **quickly**!
- Not just an API: Supabase also comes with easy-to-use **user authentication** and **file storage**
---

So Supabase is a service that allows developers to easily and quickly create a backend with a complete Postgres database. Supabase will automatically create a database and a matching API so that we can very easily request and receive data from the server. So where the Postgres database is actually hosted.

So instead of having to go through the complicated process of building  a whole backend and setting up a database ourselves, we simply let Supabase take care of all this, So it's all included and automatic, no backend development needed, which is perfect for front end developers who just want to quickly get up and running with a new project.

Supabase is actually more than just an API. It's actually a complete solution that also includes user authentication and file storage and again, all accessible from an API or from their own JavaScript library. 

So with this, we can essentially build full stack application without knowing anything about backend development.

## What is React Query
- Powerful library for managing **remote (server) state**
- Many features that allow us to write a **lot less code**, while also **making the UX a lot better**:
	- Data is stored in a cache
	- Automatic loading and error states
	- Automatic re-fetching to keep state synced
	- Pre-fetching
	- Easy remote state mutation (updating)
	- Offline support
- Needed because remote state is **fundamentally** different from regular (UI) state
--- 

**React Query** -> React Query is essentially a very powerful library for **managing remote state**. So, state that is basically stored on a server and that we need to load into our application.

So, the most fundamental thing about React Query is that all remote state is cached, which means that the fetched data will be stored in order to be reused in different points of the application. So, for example, if we fetch data about cabins in Component A, React Query will fetch the data from the API. It will then store the received data in the cache, so that Component A  can use it. And then if at a later point, Component B also wants to fetch the cabin data, then no additional API request will be necessary. Instead, React Query will simply provide this same data to Component B from the cache. 

And this has a few huge advantages. First, it wastes a bit less data to be downloaded but more importantly, once the data is in the cache all other components like Component B here, can receive it instantly. So without having to show the user another loading spinner. And this creates a super responsive and fast experience for our users. Secondly, React Query also automatically gives us all loading and error states, so that we can actually focus on what matters. React Query also automatically re-fetches the data in certain situations. For example, after a certain timeout or after we leave the browser window and then come back to it. and this is super important in order to make sure that a remote state always stays in sync with the application. For example, if some other user of the app changes the remote state at some point, for example, by updating a cabin, then the application running on all other computers will have this cabin state out of sync with the newly updated state. And so, React Query can help with this as well. So, keeping everything in sync by automatically re-fetching data.

Besides, re-fetching, we can also pre-fetch data, which basically means to fetch data that we know will become necessary later, but before it is actually displayed on the screen. And a classic example of this is pagination, where with pre-fetching, we can fetch data not only for the current page, but also for the next page. This way, when the user then moves to the next page, the data will always already be there in the cache. So, without needing to display an annoying loading spinner. It's also very easy to mutate. So, to update remote state using the many tools that are built into React Query.

One of the useful features in my opinion is support for when the user becomes offline. So, in this situation, since the data is already cached as the user moves around in the app while being offline, Components A and B can still be displayed using the cached cabin data.

And lastly, we need a library with all these features because remote state is fundamentally different from UI state. It's asynchronous and usually shared by many users of the app, which makes it so that applications running in different browsers can very easily get out of sync with the remote data that is stored on a server. So, remote state has many special needs, and that's the reason why we use something like React Query.

## An Overview of Reusability in React
### How To Reuse Code In React?
- ![[Pasted image 20250811132301.png]]
--- 

We can either re-use pieces of **UI**, or we can re-use **stateful logic** so logic that contains at least one React hook no matter which one. There is also a third category which is simply using some non-stateful logic, but for that we can simply use normal JavaScript functions. For React what matters is how we re-use **UI** and **stateful logic**. 

So as we already know to re-use pieces of the UI we use components and props and the idea is that we use props basically as an API for the components. So as a way of interacting with a component from the outside so we can customize how it works and what it looks like. taking this idea one step further, we can even pass in content or other components into components, simply by using the slightly more advanced but extremely useful `children` prop. So basically in order to customize not only what a component looks like but also the content itself.

 Moving on to re-using the stateful logic, we can re-use stateful logic simply by writing our own custom hooks. So again custom hooks allow us to write our own React hooks, which are composed of any number of any other hooks.

What if we need to re-use visuals and stateful logic at the same time in some more advanced ways. Well that's where more advanced patterns come into play. So one of these advanced patterns that developers came up with is so called **Render Props Pattern**(they aren't Reacts features), instead they are simply clever ways of using React that have emerged over time in order to solve certain problems.

With Render Props the user of the component has complete control over what component actually renders by passing in a function as a prop. So this function basically tells the component what and how to render, and the beauty of this is that with this pattern we can re-use logic that has some UI, so some JSX attached to it while giving the component the ability to receive even more JSX.

This pattern was actually super common in the old days before React hooks, because it was basically the only way of sharing stateful logic across different components, but today for that we already have custom hooks, so now this pattern isn't as common as it was before. However it still very useful and very important for certain situations in which we really do want to re-use some logic that has some UI attached to it.

For the second pattern we have the **Compound Component Pattern**, and compound means in this context that we will have multiple components that play together in order to create one big, let's call it super component which is then the **Compound Component**. and this pattern allows us to build extremely self-contained components that need to, or that want to manage their own state internally, so without that state being necessary inside the parent component that uses the compound component.