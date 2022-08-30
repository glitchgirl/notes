# Web Components

- Web platform APIS
- Custom Elements
  - can name these elements anything that doesn't clash with standard HTML tags
  - make a custom class that extends HTML
  - if you put a style tag in the component it will affect components outside of the custom component, use shadow dom
  - Life cycle methods
    - Constructor - runs when component is init
    - connectedCallback
    - disconnectedCallback
    - attributeChangedCallback
- Shadow DOM
  - used to self contain components
  - attachShadowDOM
  - shadowRoot
  - slot
- HTML Templates
  - defines the HTML, lets you customize the components
