# MedConnect API

The Express/TypeScript backend for [MedConnect’s patient frontend](https://github.com/omerdikyol/MedConnect). It stores users, doctor availability, appointments, and uploaded analysis metadata in MongoDB.

This repository is a fork of [the upstream server](https://github.com/LucaStefan112/MedConnect-Server). Preserve upstream attribution when using or describing the code; the fork is part of a shared project history.

## Local development

```sh
git clone https://github.com/omerdikyol/MedConnect-Server.git
cd MedConnect-Server
npm install
npx tsc
```

Configure `.env` for your own environment before starting: [the database connection](src/db/connection.ts) reads `USERNAME` and `PASSWORD` and contains a project-specific MongoDB connection target. [The server entry point](src/index.ts) reads `PORT`; authentication utilities use `APP_SECRET`. Adapt the connection target for your own database rather than assuming credentials alone make it portable.

```sh
npm start
```

For development, run `npm run tsc:w` in one terminal and `npm run start:dev` in another. The latter watches the compiled `build` output.

## API organization

- `/users`: registration and user routes.
- `/doctors`: doctor-related routes.
- `/appointments`: scheduling and appointment actions.
- `/analyses`: upload and analysis routes.
- `/specialisations` and `/check-auth`: lookup and authentication helpers.

[Routes](src/routes), [controllers](src/controllers), and [models](src/models) show the request-to-database flow. The current `npm test` script is a placeholder, not a backend test suite. Treat this as a development case study and review role assignment, ownership checks, and upload handling before a public deployment.
