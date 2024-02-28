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

> [!NOTE]
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
│   ├── lib --> Libraries and functions
│   │   └── utility.js
│   └── routes --> routes for every page
│       ├── +page.svelte
│       ├── newsletter
│       │   ├── +page.svelte
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

> [!NOTE]
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

 ```JSX
      <Button
          text="2"
          backgroundColor={CodingSkills === 2 ? "#C4C4C4" : "#FFFFFF"}
          width="113px"
          height="113px"
          border="2px solid black"
          fontSize="4em"
          on:click={() => {
            CodingSkills = 2;
          }}
      />
 ```

 ## Routing :
 
 ### Routing pages
 Routing is done using the `svelte-routing` package. You can find the routes in the `src/routes` folder.
 To create a new route, Create a new folder/directory with the name of the route, and create a file called `+page.svelte` inside the folder.

 ```bash
   src/routes
   ├── +page.svelte --> root page
   ├── newsletter --> newsletter route
   │   ├── +page.svelte --> file for the newsletter page
 ```

 ### Error pages

 To create an error page, create a file called `+error.svelte` in the `src/routes` folder.

 > [!NOTE]
 > The error page is used to display an error message when the user triggers an error somehow. For example, when the user tries to access a page that does not exist, the error page will be display on project level like the example below :

 ```HTML
   <script>
      import { page } from '$app/stores';
   </script>

   <h1>{$page.status}: {$page.error.message}</h1>
 ```


 ```bash
   src/routes
   ├── +error.svelte --> error page
 ```

 please  
 ```bash
   src/routes
   ├── +page.svelte --> root page
   ├── newsletter --> newsletter route
   │   ├── +page.svelte --> file for the newsletter page
   └── +error.svelte --> error page
 ```

 ------------------------------

 For more information, refer to the [documentation](https://svelte.dev/docs/introduction) and if you have any questions, feel free to reach out on Discord with the ID `sleepy_x` or here on github.

 Happy coding! 🚀.