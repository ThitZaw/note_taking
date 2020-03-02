# OpenAPI / Swagger Resource List for API Developers - Runscope - Medium

Created By: Thit Zaw
Last Edited: Feb 26, 2020 9:47 PM
URL: https://medium.com/runscope/openapi-swagger-resource-list-for-api-developers-9f6d769d9c9d

![1*DC8LfKVdUT-9fYO4JzuUrA.png](OpenAPI%20Swagger%20Resource%20List%20for%20API%20Developers%20R/1DC8LfKVdUT-9fYO4JzuUrA.png)

Update 06/06/18: Check out [openapi.tools](http://openapi.tools/) for another great resource on OpenAPI tools.

The OpenAPI Specification, formerly known as Swagger Specification, is a simple yet powerful way of describing RESTful APIs, in a machine and human readable format, using JSON or YAML. It has a large ecosystem of tools that can help you design, build, document, test, and visualize your APIs.

Here’s what a “Hello, World” example looks like:

The OpenAPI spec seems to be the most popular option among the three major formats the community is currently using for describing APIs ([RAML](http://raml.org/) and [API Blueprint](https://apiblueprint.org/) being the two others). It is used by companies of all sizes, including Microsoft, Netflix, IBM, and Lyft, to name a few.

The three major benefits of creating and using an OpenAPI specification are:

- **Generating interactive documentation** — API documentation is often overlooked, but it’s crucial for developers to understand how to interact with your endpoints, whether they’re internal or external code.
- **Human readable and machine readable** — The choice of JSON and YAML as the accepted formats is not by accident. Being language-agnostic is an important aspect of the OpenAPI specification widespread use, allowing teams to easily read and share them, while making it easy to create tooling around it for any programming language.
- **Creating SDK for multiple languages** — A big challenge that API companies face is providing client libraries for multiple languages and frameworks: Node.js, C#, Python, Ruby, Java, etc., the list could go on forever. OpenAPI tooling such as [swagger-codegen](https://github.com/swagger-api/swagger-codegen) can help you do that with little work.

Another benefit of the OpenAPI specification is that it does not require you to rewrite your existing API. You can even find unofficial specs for public APIs. However, OpenAPI is not a one-size-fits-all solution. Not all services can be described by the OpenAPI specification, and it was not intended to cover every possible case of RESTful APIs.

The Swagger specification development started in 2010, by [Wordnik](http://www.wordnik.com/about). It was later acquired by [SmartBear](https://smartbear.com/news/news-releases/sponsorship-of-swagger/), in 2015. In that same year, SmartBear created the [OpenAPI Initiative](https://www.openapis.org/) (OAI) under the Linux Foundation, and [donated the Swagger specification to it](https://www.programmableweb.com/news/%E2%80%8Bsmartbear-linux-foundation-launch-open-api-initiative-to-evolve-swagger/2015/11/10), in order to advance a common standard across industries. A number of tech companies, including Google, IBM, and Microsoft, signed on as founding members of the OpenAPI Initiative, and the Swagger Specification was rebranded as the **Open API Specification**.

Crafting good APIs is no easy task. OpenAPI brings a lot of benefits to this process, whether you approach it from a design-first or code-first perspective. The ecosystem of tools can help you generate interactive documentation, SDKs for your APIs in multiple languages, and server stubs.

But getting started with OpenAPI can be challenging. Figuring out how to start writing a spec from the ground up or for existing APIs, which tools, cloud providers, and frameworks support the specification, the differences between 1.2, 2.0, and the upcoming 3.0 versions, and finding open-source generators for your SDKs are only a few of the questions you can run into.

That’s why we decided to aggregate the best resources in a single place, and hopefully, guide you on this journey in implementing and making the most of your OpenAPI specification.

We broke down this guide into the following topics:

- Writing Spec / Design
- Documentation
- Generators
- Servers
- Clients
- Testing & Monitoring
- Gateways / Management
- Public Specifications

We really hope you find this useful, and please let us know if you think there are any additional resources we can add here.