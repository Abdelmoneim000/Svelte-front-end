# create-svelte

Everything you need to build a Svelte project, powered by [`create-svelte`](https://github.com/sveltejs/kit/tree/main/packages/create-svelte).

## Get started

1. clone this repository into your local machine

```bash
git clone https://github.com/Abdelmoneim000/Svelte-front-end.git
```

2. change directory to the project folder

```bash
cd Svelte-front-end
```

## Developing

Once you've created a project and installed dependencies with `npm install` (or `pnpm install` or `yarn`), start a development server:

```bash
npm run dev

# or start the server and open the app in a new browser tab
npm run dev -- --open
```

## Building

To create a production version of your app:

```bash
npm run build
```

You can preview the production build with `npm run preview`.

> To deploy your app, you may need to install an [adapter](https://kit.svelte.dev/docs/adapters) for your target environment.

## Testing

### For Unit Testing

```bash
npm run test
```

### For Manual and UI Testing

```bash
npm run test:ui
```

[!NOTE]
> The module for UI testing is still in consideration. It is not yet implemented.

## File Structure

```
.
├── README.md
├── package-lock.json
├── package.json
├── src
│   ├── components  --> Re-usable components. Will be used in pages
│   │   ├── Button.svelte
│   │   ├── Header.svelte
│   │   └── ...
│   ├── pages --> Pages for the website
│   │   ├── Home.svelte
│   │   ├── About.svelte
│   │   └── ...
│   ├── lib --> Libraries and functions
│   │   └── utility.js
│   └── routes --> routes for every page
│       ├── index.svelte
│       ├── about.svelte
│       └── ...
├── static --> assets
│   └── favicon.png
├── tests --> This is where the tests are located
│   ├── unit
│   │   ├── Button.test.js
│   │   ├── Header.test.js
│   │   └── ...
│   └── ui
│       ├── home.test.js
│       ├── about.test.js
│       └── ...
├── svelte.config.js
└── vite.config.js
```

[!NOTE]
> Next section for devs who are going to work on this project

## Components used :

 - Inside the `src/components` folder, you will find multiple components that are used in the pages. These components are re-usable and can be used in any page.

 - To use a component, Navigate the the page you want to use the component in, and import the component from the `src/components` folder.

 ```HTML
 <script>
    import Button from '../components/Button.svelte';
 </script>
 ```

 - Then, you can use the component in the page.

 ```HTML
    <button class="button" style="--color: {color}; --border: {border}; --boxShadow: {boxShadow};">{text}</button>
 ```

 ------------------------------