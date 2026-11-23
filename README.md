# CvSU Mini Store – Guide Questions

## 1. What is the difference between props and state?
Props are data passed into a component from its parent, and the component only reads them. State is data a component owns and manages itself, and it can change over time (like `cartCount` in `App`). When state changes, the component re-renders.

## 2. Why can a child component not modify the props it receives?
Props are read-only so data flows in one direction, from parent to child. The parent owns that data. If a child could change its props, the parent's data could be altered unexpectedly, which would make the app hard to predict and debug. A child that needs a change must ask the parent through a function.

## 3. How does the onAddToCart callback allow data to flow from child to parent even though props only flow downward?
The parent (`App`) defines `handleAddToCart` and passes it down as the `onAddToCart` prop. This is still a downward flow, but what travels down is a function. When the button is clicked, the child calls that function with the product title as an argument. The function runs in the parent, so it receives the title and updates the cart count and last added item.

## 4. Why is the key prop required when rendering a list with .map()? What could happen if it is missing or duplicated?
React uses `key` to identify each item in a list so it can tell which items were added, removed, or changed, and update only those. If keys are missing, React warns and falls back to using the item's position. If keys are duplicated, React cannot tell the items apart. This can cause wrong or stale items to be updated, mixed-up component state, and unnecessary re-renders.

## 5. What does the children prop allow you to do that a normal prop does not?
A normal prop is passed as an attribute, usually a simple value such as a string or number. `children` is whatever is nested between a component's opening and closing tags, so it lets the parent pass in JSX markup. In this project I wrapped a `<span>New</span>` or `<span>Sale</span>` badge inside `<ProductCard>`, and the card displays it without needing a separate prop for it.