- Start Date: 2020-07-31
- RFC PR: (leave this empty)
- Literal Issue: (leave this empty)

# Summary

**Literal** is a full stack JavaScript library for creating component based websites. In the growing, complex ecosystem of web development Literal draws inspiration from popular modern JavaScript libraries but aims to prioritize interface simplicity, standardization, performance, and user experience.

This is a high level view to outline a basic proposal. Thorough details about architecture and technology are captured in separate RFCs per feature.

# Motivation

While popular JavaScript libraries like React have revolutionized software engineering, some of their core characteristics impose inherent challenges to end users. The level of challenges these libraries impose can become blockers in creating web applications fit for today's standards. Literal takes alternative approaches to prioritize ease of development and optimal user experience.

### Main Incentives

- **To help engineers create performant websites that rank well in search engines**. [Google will prioritize page experience](https://webmasters.googleblog.com/2020/05/evaluating-page-experience.html) in its search algorithm. Literal focuses on performance first by utilizing tools like [Lighthouse](https://developers.google.com/web/tools/lighthouse) and [Web Vitals](https://github.com/GoogleChrome/web-vitals) to ensure performance optimization.
- **To provide an easy to learn API**. Literal is easy to learn and teach for engineers of all levels.
- **To provide a simple path for migration**. Literal draws inpiration from popular modern JavaScript libraries to provides similar tools, APIs and effectively a straightforward path for migration.
- **To generate a large, supportive contributor base**. Literal will strive to generate a large, supportive contributor community to ensure it doesn't become another project that fizzles out, leaving adopters to fend for themselves.

### Differences from Popular Frameworks

- **A "literal" DOM** (server-side rendering by default): Libraries like React and Vue use a [virtual DOM](https://reactjs.org/docs/faq-internals.html) - a "virtual", entirely separate instance of a DOM tree kept in memory and synced with the "real" DOM by a process called reconciliation. Libraries like React and Vue don't support server-side rendering out of the box at the time of this writing. Engineers concerned about SEO, for example, typically establish server-side rendering by utilizing frameworks like Next.js on top of React. Managing server-side rendering and a virtual DOM as apps scale typically results in long running client-side hydration, impossible challenges of maintaining universal parity, and high memory consumption. The cost of virtual DOM [reconcilliation](https://reactjs.org/docs/reconciliation.html) is not worth the value. Literal provides the good things about a virtual DOM without the over-engineering. It manages a real, "literal DOM" and **reconciles state to prevent unnecessary renders**. With this approach memory and distributed JS file size bloat is prevented.
- **Opinionated**: While some JavaScript libraries like React highlight an unopinionated, flexible characteristic - Literal focuses on establishing an opinionated, **standardized** framework. React requires the end user to "shop" for solutions that can lead to "dependency hell" in which a variety of dependencies and versions of dependencies conflict. *State management* is a good example that can cause this situation. To handle global state React engineers need to choose between the core Context API, or Redux, Sagas, RxJS, etc, etc. Many of these libraries add significant bytes to parse in JavaScript which degrades website performance dramatically along with a variety of complexities in testing and integration. By establishing a standardized open-source library, solutions like state management are nurtured and grown over time by a community of engineers working towards a single goal.
- **Simple, stable APIs**: Between its component lifecycle, functional vs class components, state management, hooks API and more, React is difficult to understand and learn. Literal aims to take a simpler, standard approach in its APIs so engineers can grow with the library. Literal is easy to teach and learn.

### Similarities to Popular Frameworks

- **Component based**: Literal provides a component driven API similar to libraries like React and Vue.
- **Declarative**: One of the key ingredients of an easy to learn, maintainable and scalable library is a declarative API. Literal provides a JSX-like syntax for component definition and encourages static typing by utilizing tools like Typescript in its core.
- **Unidirectional data flow**: Similar to React, components recieve read-only data.
- **State**: Despite some differences, Literal shares the concept of state.

# Detailed design

Each feature of Literal should have a corresponding RFC with a detailed design. Below are some of the core proposed features.

- **Documentation Server**: Each feature should be documented in a modern, sophisticated interface.
- **JSX-like API**: Literal components accept a state payload similar to `props` in React. State is managed outside of the component. Literal components are always "dumb" in that they only receive data, bind handlers and render. Literal doesn't do anything more than JSX - it does less. These JSX-like components are rendered universally by default (client-side and server-side).
- **State Management**: State management is a part of Literal core to promote standardization and maturity of the framework.
- **Styling**: A standardized approach to styling with modern best practice and optimal performance.
- **Build Tooling**: Literal will provide all the tools necessary to establish optimized builds.
- **Dev and Production Server**: Generating static files is supported but also a standard server. This server should support both dev and production modes.
- **Unit Testing Framework**: Literal will provide a framework for unit testing components and state.

# Drawbacks

- Order of operation in building an entire library will be quite challenging and risks contributor time investment.
- Uncertainty in driving contributor support. In order to effectively maintain such a large library, we'll need to recruit a solid contributor base.
- Establishing standardization with features like styling support will be difficult.
- Technical challenges in creating each of the features above will be quite intense.

# Adoption strategy

A roadmap documented in the [Literal project](https://github.com/foo-software/literal) will drive development of each feature. Each feature will have its own RFC.
