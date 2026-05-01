
This architecture introduces  a new approach to creating React components by dividing them in two distinct types:
-  Server components
-  Client components

Server Components
- By default, Nextjs treats all components as Server components
- These components can perform server-side tasks like reading files or fetching data from a database
- The trade=off is that they can't use React hooks or handle user interactions

Client Components
- 