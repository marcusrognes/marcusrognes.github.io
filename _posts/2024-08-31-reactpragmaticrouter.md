---
title: React Pragmatic Router
date: 2024-08-31 10:00:00 +0200
categories: [Projects]
tags: [javascript, typescript, react, router]     
---





[marcusrognes/react-pragmatic-router](https://github.com/marcusrognes/react-pragmatic-router)

## Descriptionn

This package is a router for react, designed to be simple and lightweight, it has no dependencies, and is really simple to use:

## Getting started

```bash
npm i react-pragmatic-router
```

## Example


> The route pattern param accepts regex, in this case `:someParam` is short hand for:  `(?<someParam>[^\/]+)` and uses the resulting named group as param, and you can use multiple params and named groups as you please

`index.tsx`
```tsx
import { BrowserRouter, Route } from 'react-pragmatic-router';
import Page from './Page';

function App(){
	return <BrowserRouter>
		<Route pattern="/page/:someParam" element={({ params }) => <Page someParam={params.someParam} />} />
	</BrowserRouter>;
}
```

> Links are just simple a tags with some onClick handling.
>
> NavLinks adds the activeClass (default is "active") if the current route matches the href

`Page.tsx`
```tsx
import { Link, NavLink } from 'react-pragmatic-router';

export default function Page(props: { someParam: string }){
	return <div>
		<h1>Param: {props.someParam}</h1>
		<Link href="/some-other-page">To some other page</Link>
		<NavLink activeClass="active" exact href="/some-other-page">Navlink</NavLink>
	</div>;
}
```


## Why?

I was working on an app, and was trying to make app like page transitions with react-router, I was struggling, so I decided to peek at the source code to see if there was something simple I was missing, and frankly, was horrified by what I saw.


I ended up spending less time creating this package from scratch without dependencies, than trying to implement animations with react-router.

And implementing animations with this package is super simple



