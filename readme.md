# Modern web

This is the start of a (beginner-friendly) [monorepo](https://en.wikipedia.org/wiki/Monorepo) containing commonly used [boilerplates](https://en.wikipedia.org/wiki/Boilerplate_code). This will open up the newest technologies to people who have yet to make a website themselves. Of course, it is always recommended to learn the basics of html, css, and js first.

## Getting started

### Install a package manger

To make our lives much easier, we will need a system package manager.

| System    | Package Manager                       | Shell Command |
| --------- | ------------------------------------- | ------------- |
| macOS     | [Homebrew](https://brew.sh)           | `brew`        |
| Windows   | [Chocolately](https://chocolatey.org) | `choco`       |

### Install system tools

NodeJS gives us a javascript specific package manager called `npm`. Unlike `brew` this is for more project-specific tooling, rather than your computer/system. We will be using an **npm wrapper** called [yarn](https://yarnpkg.com/en/). Using yarn over npm is completely subjective. Yarn has just a few quality of life improvements over npm. Besides some syntactical sugar, both will work just fine. They use the same exact registry (directory of packages)!

> The `$` represents a command that is written in your terminal or powershell

```sh
$ brew install node yarn

# or for Windows
$ choco install node yarn
```

## Starting a project

We provide a few boilerplates to start in your development endeavors.

### Parcel with Sass (beginner)

[Parcel](https://parceljs.org) is a task runner and project bundler. Task runners will watch your files and perform actions when anything changes. For example, automatic browser reloading on file save. A project bundler allows you to more loosely write code. When you're ready to build your project, parcel will compile, minify, and optimise your project files. For starting out, this is all you need.

Sass is a css-preprocessor which simply means you write css with some [extra features](https://raygun.com/blog/10-reasons-css-preprocessor/). At the end of the day, you get css spit out. Gross (but actually not, it's quite efficient).

### Next with Styled Components (intermediate)

[NextJS](https://nextjs.org) is a beautiful tool for writing and deploying [React](https://reactjs.org). If you are unfamiliar with React, it can be quite a change of pace from the usual website dev. Essentially, it allows html and css to be written inside of a `js` file. This process is known as `jsx` or JavaScript XML syntax. The benefit of this is that you are able to componentalise your code. A button could include content, styles, and logic in a single file. Reusability is key when working with React. Define page layouts in one place, and use them everywhere.

When dealing with this new `jsx` concept of sandboxing elements into reusable components, there are several options for styling. For example NextJS comes with [Styled JSX](https://github.com/zeit/styled-jsx) out of the box. The syntax looks like the following:

```css
/* Aside from the first and last lines, it's normal css */
<style jsx>{`
    div {
        color: palevioletred;
        background: white;
    }
`}</style>
```

This method is strictly scoped, meaning the styles only affect the file they are written in. There are ways to write global styles, and it is encouraged to read through the documentation for more info.

For this guide, however, we will be using [Styled Components](https://www.styled-components.com).

The main differences are syntax and scoping. Let's view a barebones react components:

```js
const HelloWorld = () => <div>Hello World</div>;
```

Let's first look at how we would add Styled JSX:

```js
const HelloWorld = () => (
    <div>
        Hello World

        <style jsx{`
            div {
                color: palevioletred;
                background: white;
            }
        `}</style>
    </div>
);
```

Now let's change this to use Styled Components:

```js
const HelloWorld = () => <StyleWrapper>Hello World</StyleWrapper>;

const StyleWrapper = styled.div`
  color: palevioletred;
  background: white;
`;
```

Notice how the StyleWrapper is it's own component. This fits into React's component-based model nicely.

Styled Components supports nesting, and other features similar to Sass.
