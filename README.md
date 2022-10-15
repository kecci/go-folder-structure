# Go Folder Structure

## Table of Contents
- [Go Folder Structure](#go-folder-structure)
  - [Table of Contents](#table-of-contents)
  - [Folder Structures](#folder-structures)
  - [I. Version Based Structure](#i-version-based-structure)
  - [II. Layered Based Structure](#ii-layered-based-structure)
  - [III. Function Based Structure](#iii-function-based-structure)
  - [Final thought](#final-thought)
  - [Related discoveries](#related-discoveries)

## Folder Structures

> Folder structure is Foundation of services. The good foundation is have a modularity, flexible, simple, cleanly. As a home of code.

There is 2 ways to Folder Structure:
1. Version Based Structure
2. Layered Based Structure
3. Function Based Structure

## I. Version Based Structure

Format:
- `[ServiceName][Version][DomainName][LayerName]` - PackagesName

Example:
- EcommerceService/V1/Products/Controller - (v1/controller)
- EcommerceService/V1/Products/Service - (v1/service)
- EcommerceService/V1/Products/Repository - (v1/repository)
- EcommerceService/V2/Products/Controller - (v2/controller)
- EcommerceService/V2/Products/Service - (v2/service)
- EcommerceService/V2/Products/Repository - (v2/repository)


The folder structure look like this:
```
|- EcommerceService
    |- V1
        |- Products
            |- Controller
            |- Service
            |- Repository
    |- V2
        |- Products
            |- Controller
            |- Service
            |- Repository
```

Suitable for:
- Project or Product Based, like building e-commerce, internal service, or integrations service.
- The format of folder breadcrumb will be same like API URL. (GET https://ecommerce.com/v1/products)
- Isolated per-version.
- Private projects.

Pros:
- We could build new versions, without changing the old version.

Cons:
- Should rewrite bundled code.

## II. Layered Based Structure

I found this structure on [Mindinventory](https://www.mindinventory.com/blog/golang-project-structure/).
On the github: https://github.com/Mindinventory/Golang-Project-Structure

Format:
- `[ServiceName][DomainName][LayerName][Version]` - PackagesName

Example 1:
- EcommerceService/Products/Controller/V1 - (v1controller)
- EcommerceService/Products/Controller/V2 - (v2controller)
- EcommerceService/Products/Service/V1 - (v1service)
- EcommerceService/Products/Service/V2 - (v2service)
- EcommerceService/Products/Repository/V1 - (v1repository)
- EcommerceService/Products/Repository/V2 - (v2repository)

The folder structure look like this:
```
|- EcommerceService
    |- Products
            |- Controller
                |- V1
                |- V2
            |- Service
                |- V1
                |- V2
            |- Repository
                |- V1
                |- V2
```

Suitable for:
- SDK or Library Packages use, like echo/v1 or echo/v2
- The format of folder breadcrumb will be same like import packages. (github.com/echo/echo/v1)
- Open to any versions.
- Public projects.

Pros:
- We can use cross between versions.

Cons:
- We have to aware of all the versions is impacted.

## III. Function Based Structure

Source: https://stackoverflow.com/questions/29611240/best-folder-structure-for-versioning-with-restify

Format:
- `[ServiceName][DomainName][LayerName]` - FuncName

Example 1:
- EcommerceService/Products/Controller - (funcV1/funcV2)
- EcommerceService/Products/Service - (funcV1/funcV2)
- EcommerceService/Products/Repository - (funcV1/funcV2)

```
|- EcommerceService
    |- Products
            |- Controller (V1/V2)
            |- Service (V1/V2)
            |- Repository (V1/V2)
```

Suitable for:
- Small services like microservices with no complicated or dependencies.
- The format of folder breadcrumb will be global.
- Monolithic Way.
- Any small projects.

Pros:
- There is no changes on project foldering. Only file.

Cons:
- Have a bunch of file.

## Final thought
The best folder structure is it depends on your projects. If you are building Public/Open to many access to your service you can choose the `Layered Based Structure`. If you are building a big software project, which have to bundled changes, you can choose `Version Based Structure`.

## Related discoveries
- Microservice Versioning: https://www.codeguru.com/dotnet/best-practices-versioning-microservices/

Kecci, Copyright.