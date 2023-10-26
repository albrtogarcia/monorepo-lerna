# Monorepo system with Lerna and Federation

This project is a proof of concept to show how to create a module federation micro frontend system with React and Webpack. The primary use case for module federation is the distribution of software at runtime on both client and server. This is a great fit for micro frontends, where we want to load different parts of the application from different servers and components sharing can be bidirectional, that is, an application can expose and import components at the same time.

## Why monorepo?

A monorepo is a single repository containing multiple distinct projects (packages, services, etc.) with well-defined relationships between them (microfrontend, e.g.).

The purpose of the monorepo architecture is to bring all services or packages of a project under a single repository. These projects or codes can be related or independent and can be owned by different teams. [Monorepo](https://monorepo.tools/#what-is-a-monorepo) is not monolithic, it is a single repository that contains multiple projects that can be orchestrated (dev, build, install, etc.) from the root.

[Lerna](https://lerna.js.org/) is a build system for managing and publishing multiple JavaScript packages from the same repository. Lerna runs a command against any number of projects involved in a monorepo.

## Documentation

- [Lerna](https://lerna.js.org/)
- [Monorepo](https://monorepo.tools/)
- [Webpack Module Federation](https://webpack.js.org/concepts/module-federation/)
- [Module Federation examples](https://github.com/module-federation/module-federation-examples)
- [Git submodules](https://www.atlassian.com/git/tutorials/git-submodule)
- [React](https://reactjs.org/)
- [React Router](https://reactrouter.com/)

### File structure

```
This folder (name it as you want)
  │
  └─ 📁 apps (standalone apps)
  │
  └─ 📁 packages (shared services and packages)
  │
  └─ package.json
  │
  └─ lerna.json
```

## How to use

Clone this repo with submodules:

```bash
git clone --recurse-submodules https://github.com/albrtogarcia/federation-micro-frontend.git
```

Run the following commands in the root directory to install all dependencies for all services an once and start all services:

```bash
yarn
yarn dev
```

All apps are independently deployed and served. You can access them at:

- `app-container`: http://localhost:4000
- `library`: http://localhost:4001
- `auth`: http://localhost:4002
- `service`: http://localhost:4003

## Workflow

- Production branch: `main`
- Staging branch: `staging`
- Development branch: `develop`
- Feature branches: `feature/feature-name`

## Disadvantages

Hot reloading is not working. If you change something in the library, you have to restart the container app to see the changes. This is because the library is not a dependency of the container app, but a remote module. It have to be a way to solve this problem, but I haven't found it yet, feel free to open a PR if you know how to solve it.
