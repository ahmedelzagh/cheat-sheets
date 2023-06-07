## Getting Started with NextJS and Essesntial Knowledge

### 1- Install NextJs

- To install NextJS run the following command:
```shell
npx create-next-app@latest
```
- Then you will be asked for the name of your project, and then whether you want to create a TypeScript project.

### 2- NextJS Folders structure
```js
src
├── .next // is generated when running build or dev commands
├── styles
│   ├── globals.css // contain some global css configurations
│   └── Home.module.css // css module for styling the Home Page
├── pages // responsible for the routing in the App
│   ├── api // to create APIs for the application
│   │   ├── hello.js // a testing api
│   └── _app.js // responsible for the App layout
│   └── index.js // the file that will be served on the localhost.com/
│   └── _document.js // responsible for defining the overall structure of the HTML document
├── public // contains all public resources for the App (icons, images, svgs, ...)
├── next.config.js
```

### 3- Creating a New Route
- You can create a route by creating a new file with the name of your desired route in the ***pages*** folder:
```js
├── pages 
│   ├── news.js
```
This page will be available at `localhost.com/news`

- Or you can create a folder with the name of the route you want that contains an index file inside:
```js
├── pages 
│   ├── news
│   │   ├── index.js
```
That will be also available at `localhost.com/news`

### 4- Creating a Dynamic Route
- You can create a dynamic route by using the name you want inside a square brackets:
```js
├── pages
│   ├── news
│   │   ├── [newsId].js
```
When visiting `localhost.com/news/any-id` you will see the contents of `[newId].js`
- Same applies to the folder structure method:
```js
├── pages
│   ├── news
│   │   ├── [newsId]
│   │   │   ├── index.js
```

### 5- Extracting Dynamic Parameter Values
- You can Extract the values of the parameters passed to a Dynamic Route like its ***id*** by using the ***useRouter*** hook provided from ***next/router***:
```jsx
import { useRouter } from "next/router";

export default function ProductId() {
  const router = useRouter();
  const productId = router.query.ProductId
  return <div>This is the product id: {productId}</div>;
}
```


### 6- Linking Between the Pages
- If you navigate to the news route using the `anchor` tag, the server will be requested to load the news page. This is not how a **SPA** should work:
```jsx
export default function Products() {
  return (
    <div>
        <h1>This is the latest News:</h1>
        <ul>
            <li>
                <a href='/news/article-95'>
                    Thats the Card of the first article
                </a>
            </li>
            <li>
                <a href='/news/article-96'>
                    Thats the Card of the second article
                </a>
            </li>
            <li>
                <a href='/news/article-97'>
                    Thats the Card of the third article
                </a>
            </li>
        </ul>
    </div>
  )
}
```

- Instead we use **Link** Component which is offered by `next/link`:
```jsx
import Link from 'next/link'
export default function Products() {
  return (
    <div>
        <h1>This is the latest News:</h1>
        <ul>
            <li>
                <Link href='/news/article-95'>
                    Thats the Card of the first article
                </Link>
            </li>
            <li>
                <Link href='/news/article-96'>
                    Thats the Card of the second article
                </Link>
            </li>
            <li>
                <Link href='/news/article-97'>
                    Thats the Card of the third article
                </Link>
            </li>
        </ul>
    </div>
  )
}
```
The **Link** Component also applies the same styles as the `<a></a>`, because it is by default renders an **anchor element**.