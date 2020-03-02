# Introducing Semiotic for Data Visualization - Elijah Meeks - Medium

[https://medium.com/@Elijah_Meeks/introducing-semiotic-for-data-visualization-88dc3c6b6926](https://medium.com/@Elijah_Meeks/introducing-semiotic-for-data-visualization-88dc3c6b6926)

**Semiotic** is a React-based data visualization framework. [You can see interactive documentation and examples here.](https://emeeks.github.io/semiotic/) It satisfies the need for reusable data visualization, without committing to a static set of charting types. **It came out of a need for a data visualization framework that let us make simple charts quickly without committing ourselves to using only those charts.** Semiotic incorporates the design and functionality of more complex data visualization methods as a response to the conversation these simple charts might begin.

I’ve been doing data visualization for a long time — so long that I’ve just finished the 2nd edition of my book, **[D3.js in Action](https://www.manning.com/books/d3js-in-action-second-edition)**. Before coming to Netflix I created data visualization in what can be thought of as one of the typical ways: bespoke and innovative and not reusable. Since coming to Netflix I’ve gained an increased appreciation for reusability and maintainability, which led me to working with React. And while I haven’t been working with React quite as long, I’ve been working on it long enough to watch it grow into the major framework it is today.

What I’ve seen is that, in industry, we need data visualization tools that allow us to approach problems with the same flexibility we have in purely custom data visualization but with the maintainability and reusability necessary for a team where not all members may be an expert in visualization. That’s not what we see today. Right now we have two kinds of libraries:

**Custom Viz:** Libraries that allow you to do anything with visual display of information, such as ggplot2, P5 and D3.

**E-Z Bake Charts:** Libraries that let you deploy a bunch of componentized charts, like Recharts and Highcharts.

The libraries that try to optimize for composability do so not in visual display of information, but in chart components, like axis and legend pieces. They let you construct a chart from pieces but ironically just add work to enable features that should be available on almost every chart. Or they follow a declarative pattern and try to integrate code via custom templating languages or `eval` statements.

I’m a D3 expert, so I love the full control and flexibility of D3, but not everyone can or wants to be that kind of expert. And even as an expert, I’m not going to spend the time and touch necessary to make the kind of custom work that catches eyes out in the freelancing world. In industry, data visualization developers are not expected to be auteurs, who disappear into their cave and return with a beautiful finished product. Instead, they’re expected to be part of an ongoing conversation, continuously developing an analytical application until it best reveals the underlying patterns.