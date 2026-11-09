# Demo Overview
Refer to the [README](../README.md) for the production project outline and flow.

## This Demo Application
The demo uses a modified tech stack to provide a client-only implementation. The demo has session only storage and will not persist data after page refresh.

# Workflow
See workflow in the [README Workflow](../README.md#workflow).

[Example Workflow](./example-case-workflow-diagram.png)

# Technology
## Frontend Technology
The Frontend is built with React and TypeScript. Routing and API requests use the Tanstack libraries. REST API calls use a mock service worker so that they could be swapped for an actual service in the future. The UI design uses Material UI components. 

The UI follows a Container-Presentational pattern.

### Tech list
- Vite
- React
- TypeScript
- Tanstack Router
- Tanstack Query
- Material UI components


## Backend Technology
The backend functionality is mocked. The client application will mock endpoints so that a backend could be hooked in at a future date. Data will not persist and be stored in memory.