# Performance: Part 2

## Code Splitting

Code splitting in JavaScript is a technique used to optimize the performance of web applications by splitting the application's code into smaller, more manageable chunks. The idea is to only load the code that is necessary for the current user's interaction, rather than loading the entire application code upfront.

When a JavaScript application is split into smaller chunks, each chunk represents a separate module or a logical unit of code. These chunks can be loaded on-demand as needed, reducing the initial loading time and improving the overall performance of the application.

Code splitting is particularly useful for large web applications that have a lot of JavaScript code. It allows developers to divide the application into smaller modules based on different routes, components, or functionalities. This way, when a user navigates to a specific page or performs a certain action, only the required code for that particular feature is loaded.

There are various methods and tools available for code splitting in JavaScript, depending on the framework or bundler being used. Some popular approaches include:

1. Manual code splitting: Developers manually identify the code modules and split them using techniques such as dynamic imports or lazy loading. This approach requires explicit configuration and can be more time-consuming.

2. Bundler-based code splitting: Modern JavaScript bundlers like Webpack and Rollup provide built-in features for code splitting. They analyze the application's dependencies and automatically split the code into smaller chunks during the build process.

3. Framework-specific code splitting: Some JavaScript frameworks, such as React and Vue.js, have their own mechanisms for code splitting. They offer features like dynamic imports or route-based code splitting, which allow developers to define code-splitting points within the application's source code.

By using code splitting effectively, developers can significantly improve the initial load time of their applications, enhance the user experience, and reduce the amount of unnecessary code being loaded upfront.

Here are a couple of examples to illustrate code splitting in JavaScript:

1. Manual Code Splitting with Dynamic Imports:
```javascript
// App.js
const button = document.getElementById('loadButton');

button.addEventListener('click', () => {
  import('./module')
    .then(module => {
      // Code in the 'module' is loaded dynamically
      module.doSomething();
    })
    .catch(error => {
      console.error('Error while loading module:', error);
    });
});                                                      b  /


```
In this example, the code is split manually using dynamic imports. When the button is clicked, the code inside the `module.js` file is loaded dynamically and executed.

2. Framework-Specific Code Splitting with React Router:
```jsx
import React, { Suspense } from 'react';
import { BrowserRouter as Router, Route, Switch } from 'react-router-dom';

const Home = React.lazy(() => import('./components/Home'));
const About = React.lazy(() => import('./components/About'));
const Contact = React.lazy(() => import('./components/Contact'));

function App() {
  return (
    <Router>
      <Suspense fallback={<div>Loading...</div>}>
        <Switch>
          <Route exact path="/" component={Home} />
          <Route path="/about" component={About} />
          <Route path="/contact" component={Contact} />
        </Switch>
      </Suspense>
    </Router>
  );
}

export default App;
```
In this example, React Router is used for route-based code splitting. The components (`Home`, `About`, and `Contact`) are imported lazily using React's `lazy` function and `import()` syntax. This ensures that each component is loaded only when the corresponding route is accessed, resulting in smaller initial bundle sizes and faster page loads.

These examples demonstrate how code splitting can be implemented manually or using framework-specific features. The specific approach may vary depending on the tools, frameworks, or libraries you are using in your JavaScript project.

## Tree Shaking

Tree shaking, also known as dead code elimination, is a technique used in front-end development and JavaScript to optimize the size of the code bundle. It is particularly relevant when working with module systems like ES6 modules.

In JavaScript, when you write your code, you often import various modules or libraries to use their functionality. However, you may not end up using all the functions or variables provided by those modules. Tree shaking helps identify and eliminate the unused portions of code during the bundling process, resulting in a smaller bundle size.

Here's how the tree shaking process works:

1. Static analysis: The bundler (e.g., webpack or Rollup) performs static analysis of your code and builds a dependency graph. It identifies which modules and their specific exports are being imported and used in your application.

2. Marking unused code: The bundler marks the functions, variables, or entire modules that are not explicitly used in your application.

3. Removal of unused code: The bundler eliminates the marked unused code from the final bundle, ensuring that only the necessary code is included.

Tree shaking is possible because of the static nature of ES6 modules. Unlike CommonJS modules (require/import), ES6 modules have a statically analyzable structure, allowing tools to determine the dependencies at build time.

The benefits of tree shaking include:

1. Reduced bundle size: Removing unused code significantly reduces the size of the JavaScript bundle that needs to be downloaded by the client, resulting in faster load times.

2. Improved performance: Smaller bundles lead to faster parsing and execution of JavaScript code, improving the overall performance of the application.

To enable tree shaking, you need to use a module bundler that supports this feature, such as webpack or Rollup, and configure it appropriately. Additionally, it's important to use ES6 modules or libraries that are compatible with tree shaking, as some libraries may have side effects that prevent effective dead code elimination.

## Progressive Web Apps

A progressive web app (PWA) is a type of web application that leverages modern web technologies to provide an app-like experience to users. PWAs combine the best features of both web and mobile applications, offering the reach and accessibility of the web with the enhanced functionality and user experience of native mobile apps.

Here are some key characteristics of progressive web apps:

1. Progressive Enhancement: PWAs are designed to work across different devices and browsers, providing a consistent experience regardless of the user's platform or browser choice. They can adapt to various screen sizes and capabilities.

2. Responsive and App-like: PWAs have a responsive design that adjusts to different screen sizes and orientations. They often have a fullscreen mode, app-like navigation, and an immersive user experience similar to native mobile apps.

3. Offline Capabilities: One of the significant advantages of PWAs is their ability to work offline or in areas with limited connectivity. They can cache data and resources, allowing users to access content even when they are not connected to the internet.

4. Push Notifications: PWAs can send push notifications to users, similar to native mobile apps. This feature enables businesses to engage with their users and provide timely updates or reminders.

5. App Installable: PWAs can be installed on the user's device, just like native apps, providing a shortcut icon on the home screen or app drawer. This installation process eliminates the need to visit an app store and simplifies access to the application.

6. Secure: PWAs are served over HTTPS, ensuring that the communication between the user and the app is encrypted. This enhances security and protects users' data from unauthorized access.

7. Discoverability: PWAs can be discovered through search engines, making them easily accessible to users. They don't require installation from an app store, reducing friction and making it convenient for users to find and use the app.

Overall, progressive web apps provide a way to deliver a seamless and engaging experience to users, regardless of the device or network conditions, while still leveraging the open web standards of the internet.

### HTTPS

HTTPS stands for Hypertext Transfer Protocol Secure. It is a secure version of the HTTP protocol, which is the protocol used for communication between a web browser and a web server. HTTPS encrypts the data exchanged between the browser and the server, ensuring that it cannot be intercepted or tampered with by malicious actors. It provides a secure and encrypted connection, protecting sensitive information such as login credentials, personal data, and financial transactions.

### App Manifest

The app manifest is a JSON file that provides information about a progressive web app. It describes the app's name, icons, display mode, background color, and other metadata. The manifest file allows the browser to understand that the website can be installed as a standalone app on the user's device. It helps define how the app appears and behaves when installed, providing an app-like experience. The app manifest is crucial for creating a consistent and engaging user experience across different platforms and devices.

Below is an example of a basic app manifest for a progressive web app:

```json
{
  "name": "My PWA",
  "short_name": "PWA",
  "start_url": "/",
  "display": "standalone",
  "theme_color": "#3367D6",
  "background_color": "#FFFFFF",
  "icons": [
    {
      "src": "icon.png",
      "sizes": "192x192",
      "type": "image/png"
    },
    {
      "src": "icon.png",
      "sizes": "512x512",
      "type": "image/png"
    }
  ]
}
```

This manifest defines the name of the app, its short name, the starting URL, the display mode (standalone), the theme color, background color, and icons for different sizes.


### Service Worker
A service worker is a script that runs in the background of a web page, separate from the main web page thread. It is a key component of progressive web apps, enabling features like offline caching, push notifications, and background synchronization. Service workers act as a proxy between the web application, the browser, and the network, allowing developers to intercept network requests, cache responses, and provide offline functionality. They enable PWAs to function even when there is no network connection by caching essential assets and content, and they can update the app in the background, ensuring users always have the latest version when they revisit the app.

Service workers operate independently of the web page and can continue running even if the user closes the web app. They provide a powerful mechanism for developers to create robust and engaging experiences in PWAs by adding offline capabilities, improving performance, and enhancing user engagement through features like push notifications.

Simplified example of a service worker script:

```javascript
self.addEventListener('install', function(event) {
  event.waitUntil(
    caches.open('my-cache').then(function(cache) {
      return cache.addAll([
        '/',
        '/styles.css',
        '/script.js',
        '/image.png'
      ]);
    })
  );
});

self.addEventListener('fetch', function(event) {
  event.respondWith(
    caches.match(event.request).then(function(response) {
      return response || fetch(event.request);
    })
  );
});
```

In this example, the service worker installs by caching essential files (HTML, CSS, JS, and images) in the `my-cache` cache. When a fetch event occurs (e.g., a network request from the web app), the service worker intercepts it, checks if the requested resource is in the cache, and responds with the cached version if available. Otherwise, it fetches the resource from the network.