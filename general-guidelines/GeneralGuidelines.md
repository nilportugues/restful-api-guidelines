# General Guidelines

The titles are marked with the corresponding labels: {{ book.must }}, {{ book.should }}, {{ book.could }}.

## {{ book.must }} API First: Define APIs using  OpenAPI YAML or JSON

API First is one of our architecture principles, as per our Architecture Rules of Play.
Define, document and review your APIs before delivering them (also see API review procedure).

## {{ book.should }} Provide External Documentation

In addition to defining the API with OpenAPI, it’s good practice to provide documentation that
describes the API’s scope and purpose; architecture and use-case context (including figures);
sequence flows; edge cases and possible error situations, etc. Include a link to this documentation
using the “externalDocs” property in your RESTful API OpenAPI definition and post it online on
GitHub Enterprise pages, on specific team web servers, or as a Google doc.

## {{ book.must }} Write APIs in U.S. English

## {{ book.must }} Avoid Actions — Think About Resources

REST is all about your resources, so consider the domain entities that take part in web service interaction, and aim to model your API around these using the standard HTTP methods as operation indicators. For instance, if an application has to lock articles explicitly so that only one user may edit them, create an article lock with PUT or POST instead of using a lock action.

Request:

    PUT /article-locks/{article-id}

The added benefit is that you already have a service for browsing and filtering article locks.

## {{ book.should }} Define *useful* resources

As a rule of thumb resources should be defined to cover 90% of all its client's use cases. A *useful* resource should
contain as much information as necessary, but as little as possible. A great way to support the last 10% is to allow
clients to specify their needs for more/less information by supporting filtering and
[embedding](../hyper-media/Hypermedia.md#should-allow-embedding-of-complex-subresources).

## {{ book.must }} Keep URLs Verb-Free

The API describes resources, so the only place where actions should appear is in the HTTP methods.
In URLs, use only nouns.

## {{ book.must }} Use Domain-Specific Resource Names

API resources represent elements of the application’s domain model. Using domain-specific nomenclature for resource names helps developers to understand the functionality and basic semantics of your resources. It also reduces the need for further documentation outside the API definition. For example, “sales-order-items” is superior to “order-items” in that it clearly indicates which business object it represents. Along these lines, “items” is too general.