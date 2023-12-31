# React-Cosmos with NextJS
## Build react-cosmos on top of the main app with minimal changes.

### What does this project do?
If you are looking to use react-cosmos to generate a static style guide for your nextJS app while keeping the same codebase then this project is for you.


### How To run the main app?
You can run the main app by going to the main folder and run these commands
```
npm install
npm run dev
```
the app will run in dev mode on port `3000`. You can check nextJS documentations to see how to build the app or deploy it to vercel.


### How To run and build react-cosmos
You will need to go to the folder `.cosmos` and run these commands
```
cd .cosmos
npm install
npm run cosmos-export
npm run build
npm start
```
Cosmos will generate the static pages for all the fixture and create the app and run it on `8080`


### Why is this different?
React-cosmos is built to run inside you main app but on a separate port and requires the app to be running as well. For instance, the main app can run on port `3000` and react-cosmos on port `5000`. Then react-cosmos would iFrame the main app as a renderer and use it to render the components.

This works but if you wanted to run react-cosmos as an independent app while maintaining one codebase then it can be a bit tricky. React-cosmos documentations recommend building the full app as a static project using the nextJS settings `output: 'export'` which might not what you want to do with your app.

This project help solving this issue by running react-cosmos in a sub folder in a way that it has access to the main app's components while not affecting it in any way which help keeping the main app and react-cosmos separate.

### How to run two projects (app and react-cosmos styleguide) on vercel?
You can create two projects on vercel (one for your app and the other for vercel) and connect them to the same codebase. The main app can use the default settings for a nextJS app. However, for the react-cosmos vercel project to work, you will need to customize the build settings this way:

```
Build command: cd .cosmos && npm run cosmos-export && npm run build
Output directory: .cosmos/.next
Toggle on the option "Include source files outside of the Root Directory"
```

This way both the main app and react-cosmos can share the same codebase but create two different deployments.