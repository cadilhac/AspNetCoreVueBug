# Introduction

This small project attempts to integrate Vue into an Asp.Net Core project using Vue's SFC (Single File Component) functionality (Vue files must therefore be compiled). The App component has no template. The template is found directly in the _Layout.cshtml file (in-DOM template):

```
<div id="app">{{ message }}</div>
```

The vite.config.js file has been set up so that compilation output will go in the /wwwroot/client folder. In this config file, [Vue is also aliased so that the Vue compilation feature is loaded](https://vuejs.org/guide/scaling-up/tooling.html#project-scaffolding).

# Instructions

- In the client folder, run:

```
npm install  
npm run dev
```

- Open VueBug.sln in Visual Studio 2022
- Hit F5. It will open the browser. Hit F12 to see the console. The following warning will be displayed:

>[Vue warn]: Property "message" was accessed during render but is not defined on instance. at <App>

As the project is set up, the message variable from Vue is not found at render time. However, if Vue dev tools is installed in the browser, it will show that 'message' is set.

**Note 1:**

If a template is added in the App.vue file, like this:

```
<template>
  <div id="app">{{ message }}</div>
</template>`
```

then 'message' is correctly displayed. But this is not what is desired since the template must be in the cshtml file.

**Note 2:**

Instead of running the client on port 5000 in dev mode, it can be compiled with 'npm run build' which will create the necessary javascript files in wwwroot/client. Running the asp.net core web site in Production mode will then behave differently and still incorrectly. Even if no template is defined in the App component, the div#app node's content will be emptied. No content, no Vue warning... and so no message displayed.

# Help needed

How to fix the project so that {{ message }} in the _Layout.cshtml file is correctly replaced by the state variable defined in the App component?
