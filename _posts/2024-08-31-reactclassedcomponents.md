---
title: React Classed Components
date: 2024-08-31 10:00:00 +0200
categories: [Projects]
tags: [javascript, typescript, react]     
---



[marcusrognes/react-classed-components](https://github.com/marcusrognes/react-classed-components)

## Description

This is very similar to styled-components, but instead of css, you add css classes.

## Getting started

```bash
npm i react-classed-components
```

## Example

`index.tsx`
```tsx
import classed from 'react-classed-components';

const Wrapper = classed.main``;
const Container = classed.div`container`;
const Header = classed.header`d-flex justify-content-center py-3`;
const HeaderMenu = classed.ul`nav nav-pills`;
const NavItem = classed.li`nav-item`;
const NavItemLink = classed.a<{active?:boolean}>`nav-link ${(({params})) => params.active && "active" || ""}`;

function App(){
	return <Wrapper>
		<Container>
			<Header>
				<HeaderMenu>
					<NavItem>
						<NavItemLink href="#" active>Home</NavItemLink>
					</NavItem>
					<NavItem>
						<NavItemLink href="#">Features</NavItemLink>
					</NavItem>
					<NavItem>
						<NavItemLink href="#">Pricing</NavItemLink>
					</NavItem>
					<NavItem>
						<NavItemLink href="#">FAQs</NavItemLink>
					</NavItem>
					<NavItem>
						<NavItemLink href="#">About</NavItemLink>
					</NavItem>
				</HeaderMenu>
			</Header>
		</Container>
	</Wrapper>;
}
```


## Why?

I needed a simple way of defining components for my website, and although styled-components are amazing for component structure and SPA\`s, it gives some overhead if used for ssr or pre-rendered html.
The styling would be sent for every page, instead of being shared in css files.
