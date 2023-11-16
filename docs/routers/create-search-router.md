---
title: createSearchRouter
new: true
---

# `createSearchRouter`

This router is useful if you are not in control of the url of your application. Instead of using normal URLs, it will use the search (?) portion of the URL to manage the "application URL".
An example of this is an embedded widget that is loaded on a page that you do not control.

<docs-warning>Using search URLs is not recommended.</docs-warning>

Other than that, it is functionally the same as [`createBrowserRouter`][createbrowserrouter].

```tsx lines=[4,11]
import * as React from "react";
import * as ReactDOM from "react-dom";
import {
  createSearchRouter,
  RouterProvider,
} from "react-router-dom";

import Root, { rootLoader } from "./routes/root";
import Team, { teamLoader } from "./routes/team";

const router = createSearchRouter([
  {
    path: "/",
    element: <Root />,
    loader: rootLoader,
    children: [
      {
        path: "team",
        element: <Team />,
        loader: teamLoader,
      },
    ],
  },
]);

ReactDOM.createRoot(document.getElementById("root")).render(
  <RouterProvider router={router} />
);
```

[createbrowserrouter]: ./create-browser-router
