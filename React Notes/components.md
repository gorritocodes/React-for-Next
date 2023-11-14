# Components

User interfaces can be broken down into smaller building blocks called components.

![building blocks called components](components.avif)

Components allow you to build self-contained, reusable snippets of code. If you think of components as LEGO bricks, you can take these individual bricks and combine them together to form larger structures. If you need to update a piece of the UI, you can update the specific component or brick.

Media Component Example
This modularity allows your code to be more maintainable as it grows because you can easily add, update, and delete components without touching the rest of our application.

Rules:

- React components should be capitalized to distinguish them from plain HTML and JavaScript.
- Return a single root element
- Close all the tags. JSX requires tags to be explicitly closed: self-closing tags like \<img> must become \<img />, and wrapping tags like \<li>oranges must be written as \<li>oranges\</li>.
- camelCase all most of the things!. JSX turns into JavaScript and attributes written in JSX become keys of JavaScript objects. In your own components, you will often want to read those attributes into variables. But JavaScript has limitations on variable names. For example, their names can’t contain dashes or be reserved words like class.

This is why, in React, many HTML and SVG attributes are written in camelCase. For example, instead of stroke-width you use strokeWidth. Since class is a reserved word, in React you write className instead, named after the corresponding DOM property:
