# React Router 7 vs React 19.1.0

There is an issue in React router, where if you upgrade to react 19.1.0, YOu are unable to start the project. This issue is ONLY present when running in a monorepo, and not if you create a standalone repo for the `react-router` app.

If you run `npm i` and try to start the app `npx nx dev reprod` Will cause you to see an error in the browser and console when you try to access the app in the browser

```
Unexpected Server Error

TypeError: Cannot read properties of null (reading 'useContext')
```

If you downgrade to react `19.0.0`, and try to run the app again, it will work just fine

```json
{
  "name": "@rr7-issue/source",
  "version": "0.0.0",
  "license": "MIT",
  "scripts": {},
  "private": true,
  "dependencies": {
    "@react-router/node": "^7.2.0",
    "@react-router/serve": "^7.2.0",
    "isbot": "^4.4.0",
    "react": "19.0.0",
    "react-dom": "19.0.0",
    "react-router": "^7.2.0"
  }
  //...
}
```

Console error:

```bash
$ nx dev reprod

> nx run @rr7-issue/reprod:dev

> react-router dev

  ➜  Local:   http://localhost:4200/
Invalid hook call. Hooks can only be called inside of the body of a function component. This could happen for one of the following reasons:
1. You might have mismatching versions of React and the renderer (such as React DOM)
2. You might be breaking the Rules of Hooks
3. You might have more than one copy of React in the same app
See https://react.dev/link/invalid-hook-call for tips about how to debug and fix this problem.
TypeError: Cannot read properties of null (reading 'useContext')
    at Module.process.env.NODE_ENV.exports.useContext (C:\dev\rr7-issue\node_modules\react\cjs\react.development.js:1168:25)
    at useInRouterContext (file:///C:/dev/rr7-issue/node_modules/react-router/dist/development/chunk-QMGIS6GS.mjs:4830:17)
    at Router (file:///C:/dev/rr7-issue/node_modules/react-router/dist/development/chunk-QMGIS6GS.mjs:5747:6)
    at Object.react-stack-bottom-frame (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:8723:18)
    at renderWithHooks (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:4621:19)
    at renderElement (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5056:23)
    at retryNode (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5704:22)
    at renderNodeDestructive (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5530:11)
    at renderElement (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5434:15)
    at retryNode (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5704:22)
    at renderNodeDestructive (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5530:11)
    at renderElement (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5434:15)
    at retryNode (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5704:22)
    at renderNodeDestructive (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5530:11)
    at renderElement (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5434:15)
    at retryNode (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5704:22)
    at renderNodeDestructive (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5530:11)
    at renderElement (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5434:15)
    at retryNode (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5704:22)
    at renderNodeDestructive (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5530:11)
    at renderNode (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:6080:18)
    at renderChildrenArray (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5965:9)
    at retryNode (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5717:13)
    at renderNodeDestructive (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5530:11)
    at renderElement (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5196:13)
    at retryNode (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5704:22)
    at renderNodeDestructive (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5530:11)
    at finishFunctionComponent (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:4665:13)
    at renderElement (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5107:11)
    at retryNode (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5704:22)
    at renderNodeDestructive (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5530:11)
    at renderElement (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5042:11)
    at retryNode (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5704:22)
    at renderNodeDestructive (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5530:11)
    at renderElement (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5434:15)
    at retryNode (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5704:22)
    at renderNodeDestructive (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5530:11)
    at renderNode (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:6080:18)
    at renderChildrenArray (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5965:9)
    at retryNode (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5717:13)
    at renderNodeDestructive (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5530:11)
    at renderElement (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5196:13)
    at retryNode (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5704:22)
    at renderNodeDestructive (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5530:11)
    at finishFunctionComponent (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:4665:13)
    at renderElement (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5107:11)
    at retryNode (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5704:22)
    at performWork (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:6507:19)
    at AsyncLocalStorage.run (node:internal/async_local_storage/async_hooks:91:14)
    at C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:7131:31
Invalid hook call. Hooks can only be called inside of the body of a function component. This could happen for one of the following reasons:
1. You might have mismatching versions of React and the renderer (such as React DOM)
2. You might be breaking the Rules of Hooks
3. You might have more than one copy of React in the same app
See https://react.dev/link/invalid-hook-call for tips about how to debug and fix this problem.
TypeError: Cannot read properties of null (reading 'useContext')
    at Module.process.env.NODE_ENV.exports.useContext (C:\dev\rr7-issue\node_modules\react\cjs\react.development.js:1168:25)
    at useInRouterContext (file:///C:/dev/rr7-issue/node_modules/react-router/dist/development/chunk-QMGIS6GS.mjs:4830:17)
    at Router (file:///C:/dev/rr7-issue/node_modules/react-router/dist/development/chunk-QMGIS6GS.mjs:5747:6)
    at Object.react-stack-bottom-frame (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:8723:18)
    at renderWithHooks (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:4621:19)
    at renderElement (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5056:23)
    at retryNode (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5704:22)
    at renderNodeDestructive (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5530:11)
    at renderElement (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5434:15)
    at retryNode (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5704:22)
    at renderNodeDestructive (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5530:11)
    at renderElement (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5434:15)
    at retryNode (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5704:22)
    at renderNodeDestructive (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5530:11)
    at renderElement (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5434:15)
    at retryNode (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5704:22)
    at renderNodeDestructive (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5530:11)
    at renderElement (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5434:15)
    at retryNode (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5704:22)
    at renderNodeDestructive (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5530:11)
    at renderNode (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:6080:18)
    at renderChildrenArray (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5965:9)
    at retryNode (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5717:13)
    at renderNodeDestructive (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5530:11)
    at renderElement (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5196:13)
    at retryNode (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5704:22)
    at renderNodeDestructive (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5530:11)
    at finishFunctionComponent (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:4665:13)
    at renderElement (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5107:11)
    at retryNode (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5704:22)
    at renderNodeDestructive (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5530:11)
    at renderElement (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5042:11)
    at retryNode (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5704:22)
    at renderNodeDestructive (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5530:11)
    at renderElement (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5434:15)
    at retryNode (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5704:22)
    at renderNodeDestructive (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5530:11)
    at renderNode (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:6080:18)
    at renderChildrenArray (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5965:9)
    at retryNode (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5717:13)
    at renderNodeDestructive (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5530:11)
    at renderElement (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5196:13)
    at retryNode (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5704:22)
    at renderNodeDestructive (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5530:11)
    at finishFunctionComponent (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:4665:13)
    at renderElement (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5107:11)
    at retryNode (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:5704:22)
    at performWork (C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:6507:19)
    at AsyncLocalStorage.run (node:internal/async_local_storage/async_hooks:91:14)
    at C:\dev\rr7-issue\apps\reprod\node_modules\react-dom\cjs\react-dom-server.node.development.js:7131:31
Invalid hook call. Hooks can only be called inside of the body of a function component. This could happen for one of the following reasons:
1. You might have mismatching versions of React and the renderer (such as React DOM)
2. You might be breaking the Rules of Hooks
3. You might have more than one copy of React in the same app
See https://react.dev/link/invalid-hook-call for tips about how to debug and fix this problem.
```
