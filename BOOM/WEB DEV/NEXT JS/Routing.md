It acts like a file location but in website
It mirrors the folder structure in a website



Routing conventions:
- All routes must live inside the app folder
- Route files must be named either page.js or page.tsx
- Each folder represents a segment of the URL path
When these conventions are followed, the file automatically becomes available as a route.

Non existing routes gives 404 code

It must be in /src directory

To make a page like root/about:
- make a folder name about in /src directory and add the page.tsx file 




## Nested Routing

The conventions are:
- localhost:3000/blog 
- localhost:3000/blog/first
- localhost:3000/blog/second

here we can make a folder name blog which will have subfolders first and second with a page.tsx in each


## Dynamic Routing

The conventions are:
- localhost:3000/products
- localhost:3000/products/id
- localhost:3000/products/1

Image having hundreds of products to fix this make a folder named [productId] under products folder with page.tsx file like below

```
export default async function ProductDetails({
    params,
}: {
    params: Promise<{productId: string}>;
}) {
    const productId = (await params).productId;
    return <h1> Details about product {productID}</h1>;
}
```


## Nested Dynamic Routes

The conventions are:
- localhost:3000/products/1
- localhost:3000/products/1/reviews/1

```
export default async function ProductReviews({
    params,
}: {
    params: Promise<{reviewId: string}>;
}) {
    // component
    const {productId,reviewId} = await params;
    return <h1> Review {reviewId} for product {productId}</h1>;
}
```


## Catch-all Segments

The conventions are:
- localhost:3000/docs/feature1/concept1
- localhost:3000/docs/feature1/concept2
- localhost:3000/docs/feature2/concept1
- localhost:3000/docs/feature2/concept2

20 features X 20 concepts = 400
20 features X 1 [conceptId] = 20
1 [featureId] x 1 [conceptId] = 1

the page.tsx is in \app\docs\[...slug]
\app\docs\[[...slug]]  to show home page for  localhost:3000/docs -> last return  Docs home page

```
export default async function Docs({
     params,
}: {
     params: Promise<{slug : string[]}>;
}) {
     cont {slug} = await params;
     if(slug?.length === 2) {
     return (
     <h1> Viewing docs for feature {slug[0]} and concept {slug[1]}
     </h1>
     );
     }else if(slug?.length === 1) {
     return <h1> Viewing docs for feature {slug[0]} and concept {slug[1]} </h1>
}
     return <h1>Docs home page</h1>;
)
```


## Not Found file 

Must be in /src/not-found.tsx for global usage


```
import {notFound } from "next/navigation";
```
add it to any .tsx  and do function call by `notFound()`

this not-found.tsx can be added to any route for custom message


## File Colocation

without using `export default` the route is not visible on site and which can be used to test thing without breaking anything


## Route Groups

Let's us logically organize our routes and project files without impacting the URL structure 
Let's implement authentication routes:
- register
- login
- forgot-password

Keep all the routes inside `auth` folder 
To make it visible to `localhost::3000/login` from `localhost::3000/auth/login` 
Rename the `auth` folder to `(auth)`