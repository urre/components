---
title: Core Concepts
---


## The `as` prop
The `as` prop is a feature that all of our components get from [styled-components](https://www.styled-components.com). It allows you to pass a HTML tag or another component to a Primer Component to be rendered as the base tag of that component.


For example, say you are using a `Button` component, and you really need to apply `Flex` styles to it. You can compose `Flex` and `Button` like so:

```
<Button as={Flex}/>
```

This will allow you to use all of the `Button` props _and_ all of the `Flex` props without having to wrap your `Button` component in another `Flex` component.

This pattern does have some limitations. Say you are using a `<Button>` component and you really want it to use an `a` tag, but you also need flex props. In this case, you'd need to wrap your `Button` component in a `Flex` and use the `as` prop on `Button` to set it to an `a` tag. You cannot provide multiple values for the `as` prop.


```
<Flex>
  <Button as='a' />
</Flex>
```

One alternate way to do this is to define `Flex` using the `as` prop set to `a` and then pass the custom `Flex` to the `Button`'s `as` prop, but that can feel a bit messy:

```
const LinkFlex = <Flex as='a'/>
//in render function...
<Button as={LinkFlex}/>

```


## Responsive props
It's really easy to set different values for most of our component props based on screen size! We take advantage of [styled-system](https://github.com/styled-system/styled-system)'s responsive props API in our components.

```
<Button display={['flex', 'flex', 'none']}/>

or

<Text fontSize={[1,1,1,4]}/>
```

## Providing your own theme

You can provide your own theme to Primer Components! There are a few ways of doing this to varying degrees, checkout the [theme docs](https://primer.style/components/docs/primer-theme) for more information.

## The `css` prop
When push comes to shove and you just _really_ need to add a custom CSS rule, you can do that with the `css` prop. Please don't abuse this :)

```
<Box css='border-bottom-right-radius: 0px' />

```

## Types of components

We categorize our components into 3 general types. Building block components, pattern components, and helper components. Understanding how these types of components interact with each other can help you better understand how to get the most out of Primer Components.

- Building Blocks

 Building block components are components that are basic in their functions and can be used together with other components to build just about any UI. Some examples of building block components are `Box`, `Avatar`, `Details`, and `Link`.

 - Pattern Components

 Pattern components are components that are made up of several building block components to represent a commonly used pattern in our UI. Some examples of pattern components are `UnderlineNav` and `FilterList`. We plan on expanding our offering of pattern components in the near future.

 - Helper Components

 Helper components are components that help the user achieve common CSS patterns while maintaining some control over values used. Some examples of helper components are `Flex`, `Text`, `Grid`, and the `Position` components.