# NextJS Introduction

## What is NextJS?
**NextJS** is a popular **web development framework** built on top of **React** that helps you create fast, modern websites and applications. While React focuses on building user interfaces, NextJS adds powerful features that make it easier to build full websites from start to finish.
{ .annotate }

## What is React?
**React** is a popular **JavaScript library** used for building user interfaces, especially for web applications. It allows developers to create reusable components (small pieces of UI like buttons, forms, or entire sections) that can be combined to build complex interfaces. 

React uses a **declarative approach**, meaning you **describe** what the UI should look like **based on data**, and it efficiently updates the page when that data changes. This makes it easier to manage dynamic, interactive applications while keeping code organised and maintainable.

## NextJS Features
Here are some key features of NextJS:

- **File-based routing** – pages are created automatically from your project folders, so you don’t need to set up routing manually
- **Built-in frontend and backend support** – you can build both the website and server logic in the same project without extra setup
- **Easy data handling** – comes with built-in ways to load and use data from APIs or databases
- **Optimised performance by default** – includes automatic improvements so your site loads quickly without extra configuration
- **Built-in styling support** – works out of the box with modern styling tools like Tailwind CSS
- **Simple deployment** – can be deployed easily with platforms like Vercel/Netlify with minimal configuration

For beginners, this means you don’t have to set up everything from scratch. NextJS gives you a structured way to build real-world web apps quickly, whether you're creating a simple website or something more advanced like a dashboard or online service.

In short, NextJS is a tool that makes building complete, high-performance web applications easier and more efficient.

## Creating a NextJS Application
1. **Open a terminal** in the location where you would like to store your project.

2. **Run** the following command:
```bash
npx create-next-app@latest my-app
```

1. **Replace** `my-app` with the name of your app. You must ensure the name meets the following rules:

    - No spaces (use dashes -)
    - No uppercase letters (all lowercase)
    - Keep it simple (no long names, e.g. my-really-long-app-name-for-my-project)

3. **When prompted** to use the **recommended defaults**, select `Yes, use recommended default`. (1)
{ .annotate }

    1. This installs all the recommended default packages such as:
        - Typescript Language Support
        - Tailwind CSS Library

## Running a NextJS Application
TODO..