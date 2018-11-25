# Test React Components with Jest and `react-testing-library`

Checkout individual branches for changes specific to that section of the course.

1. **Render a React component for testing**

   ```bash
   npx jest favorite
   ```

   To mount a React component we ReactDOM and a node on which to mount it. We
   can use `document.createElement('div')` to create a mount point, and then
   evaluate that `div`'s content using query selectors.

   `HTMLInputElement.type` returns the type of the input.

   `Node.textContent` returns the text inside a DOM node and its descendants.

   ***

   Note: No need to install `babel-jest` manually if using Babel 7 as it's already
   installed when Jest is installed (see `npx jest --showConfig`). To correctly
   transpile JSX you'll need `@babel/core` and `babel-core@7.0.0-bridge.0`.
   Tests will transpile JSX without any additional libraries or config.

2. **Use jest-dom for improved assertions**

   ```bash
   npx jest favorite
   ```

   To make assertions on DOM nodes easier we can extend expect. Instead of
   getting sometimes weird errors that don't explicitly point to the problem,
   custom matchers can provide more informative errors.

   `jest-dom` is a library that does the heavy lifting for us when it comes to
   assertions on the DOM. We have two mechanisms to extend Jest's `expect`
   using `jest-dom`'s matchers:

   1. explicitly import the matchers you want from `jest-dom`, and then use
      `expect.extend(// object with names of matchers to extend)`
   2. import `jest-dom/extend-expect` to make all matchers available in the
      file

   Another option is to use Jest's `setupTestFrameworkScriptFile` to extend
   `expect` for all files.

3. **Use dom-testing-library to write more maintainable React tests**

   ```bash
   npx jest favorite
   ```

   Querying a label by its `textContent` doesn't give us any confidence in the
   label actually performing its job. If the `id` attribute is not properly
   configured, users will not get the benefit of the label.

   We can use `dom-testing-library` to write tests that can better describe how
   UIs work and do the heavy lifting for us.

   The `queries` export from `dom-testing-library` has a number of methods on
   it, one of which is `.getByLabelText` which returns an `HTMLInputElement`
   based on the `id` attribute of the `label` matching the text passed into the
   function.

   Users are not specifically concerned with the case of the `label`s text, so
   we can use an case insensitive regex to select the element.

   `dom-testing-library` has a convenient export that allows us to retrieve all
   the query methods that it exports but for a specific element.