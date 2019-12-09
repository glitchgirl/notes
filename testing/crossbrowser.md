# Cross-browser testing

- First, know what browsers you need to support and which you do not.
- Build your site using valid, standards-based HTML, CSS, and JavaScript.
- Limit yourself to only using the features that Caniuse.com says are supported fully in all of the browsers you need your site to work in.
- Try to stay as close to the browser as possible (text you write -> into the browser, as little between those two as possible).
- Try not to run your code through (to m)any tools that transform or alter the code you write before it gets to the browser. Every layer of abstraction here serves as a layer of indirection and doubt when it's time to debug, and is an additional potential point of errors.
- Test your build in more than one browser, from the outset of the project.
People get into cross-browser issues more often when they:
- Never check their site in a second browser until it's fully built.
- Rely on autoprefixer-like tools to fix or change their code to 'make their code work' in other browsers it's not written to support.
- Rely on polyfills to bring their own support for features they want to use that are missing from the browser they need to run it in (some polyfills are better than others, some are unusable disasters)

## Cross-browser testing tools

- Using chrome dev
- Using firefox

## Modernizr

It’s a collection of superfast tests – or “detects” as we like to call them – which run as your web page loads, then you can use the results to tailor the experience to the user.
