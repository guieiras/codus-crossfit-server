# Codus Crossfit Server

[![Greenkeeper badge](https://badges.greenkeeper.io/guieiras/codus-crossfit-server.svg)](https://greenkeeper.io/)

## Roadmap

### v0.1

- [X] Setup Typescript
- [X] Setup GraphQL-Yoga
- [X] Define Schema
- [X] Expose Stubbed Schema
  - [X] Expose Challenge type
    - [X] Create `DateTime` scalars
      - [Custom Scalars](https://www.apollographql.com/docs/apollo-server/v2/features/scalars-enums.html)
  - [X] Expose WIP Challenge type
- [X] Setup ORM
  - [X] Basic configuration
  - [X] Challenge Entity
  - [X] WIP Challenge Entity
  - [X] [Migrations](https://github.com/typeorm/typeorm/blob/master/docs/migrations.md)
- [X] Add Real Resolvers
  - [X] Challenges
  - [X] Challenge By Id
  - [X] WIP Challenges
  - [X] WIP Challenges By Id
  - [X] Challenge by WIP Challenge
- [X] Add Mutations
  - [X] Add Challenges
  - [X] Delete Challenges
  - [X] Update Challenges
  - [X] Add WIP Challenges
  - [X] Move WIP Challenges
  - [X] Delete WIP Challenges
- [X] Good Stuff
  - [X] Hot Reloading
  - [X] Authentication
    - [X] SignIn mutation
      - [X] Mocked Verification
      - [X] Password Verification
    - [X] SignUp mutation
      - [X] Generate migration
      - [X] Create User entity
      - [X] Save encrypted password
    - [X] Disallow normal users to execute Challenge mutations

### v0.2

- [ ] Deploy using `now`
- [ ] Common User login
  - [ ] Authorization
- [ ] Subscriptions

---

## Simple GraphQL Server with Postgraphile and Docker

1. Creating Network

    `docker network create crossfit`

2. Creating Database

    `docker run --name crossfit_db -p 5432:5432 -e POSTGRES_PASSWORD=password --network=crossfit postgres`

3. Seeding Database

    Use [Schema](./schema.sql) file to create tables and relations.

4. Starting Postgraphile

    `docker run -p 5000:5000 --network crossfit graphile/postgraphile --connection postgres://postgres:password@crossfit_db:5432/crossfit --schema public --watch`

You can export Postgraphile GraphQL schema using following command:

```bash
docker run -p 5000:5000 -v "PATH_TO_HOST:/host" --network crossfit graphile/postgraphile --connection postgres://postgres:password@crossfit_db:5432/crossfit --schema public --export-schema-graphql="/host/schema.gql"
```
