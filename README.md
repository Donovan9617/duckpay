# DuckPay

> Digital wallets for making and receiving payments using tokens and QR.

<img width="1225" alt="Screenshot 2024-07-08 at 11 38 32 AM" src="https://github.com/Donovan9617/duckpay/assets/63310319/cb0a5c2d-95fa-4d49-8a8d-9ca49bc7ad78">

## Features

1. **Retrieve wallet with key** → Users may enter secret key to retrieve all tokens in the digital wallet tagged to key regardless of device (mobile phones or even laptops).
2. **Deposit cash into DuckPay ATMs** → Users can deposit cash into DuckPay ATMs to credit tokens into their wallet via QR codes and our DuckPay Qr code scanner.
3. **Payment with tokens’ QR Code** → Senders may tap on a token with monetary value in their digital wallet and display its QR code to the merchant to make payment.
4. **Recipient of Payment with QR Scanner** → Merchants may tap on the QR scanner icon on Home page and scan the displayed QR code of token from senders to accept payment.
5. **Merging tokens** → Users can drag and drop tokens onto one another to merge multiple small token values into larger token values to be used for larger transactions.
6. **Splitting tokens** → Users can click on the Split icon and specify the split values to split large token values into multiple smaller token values to be used for smaller transactions.
7. **Theme mode** → Users can customise application theme mode to their preferences.

## Benefits

1. **Login Accounts not required** → Users do not require creating an account with their personal information to use DuckPay. Instead, they simply enter a key issued to them by DuckPay to access the wallet tagged to the key.  This key is issued to users once they have a token credited in the wallet.
2. **Bank Accounts not required** → Users do not require a bank account nor a credit card to make and/or receive payments and transactions.
3. **Recyclable Accounts** → Once a user’s wallet is out of tokens, the wallet will be deleted. A wallet is only created when a token is credited to the wallet, causing it to generate a key. Without permanent accounts, users do not have to worry about personal information.
4. **Aesthetic and Easy-to-use** → Every DuckPay feature (Key issue, QR Scanner, Wallet tokens, QR value of tokens, Merge token, Split token, Theme mode) is readily accessible on the landing page of the app through intuitive icons, cards and modals.
5. **Secure transactions** → DuckPay ensures that there is no way to steal tokens between users or modify token amounts in wallets. Additionally, once a token’s QR code has been scanned, its QR code will be invalidated, and it will be deleted from the user’s app to prevent reuse.

## Project structure

This project is a monorepo set up using [Turborepo](https://turbo.build).

```plaintext
.
├── apps
│  ├── account-service
│  ├── atm
│  ├── payment-service
│  └── web
├── deployment
│  └── nginx-config
├── docker-compose.yml
└── packages
   ├── accounts
   ├── api
   ├── config-eslint
   ├── config-typescript
   └── payments
```

* `apps` - Contains the services & applications that make up the project
  * `account-service` - The account service backend (Express.js, TypeScript)
  * `atm` - The ATM frontend application (React.js, TypeScript)
  * `payment-service` - The payment service backend (Express.js, TypeScript)
  * `web` - The frontend web application (React.js, TypeScript)
* `deployment` - Contains the deployment configurations for the project
  * `nginx-config` - Contains the Nginx configuration for the project
* `docker-compose.yml` - The Docker Compose configuration for the project
* `packages` - Contains the shared packages used across the project
  * `accounts` - Contains the account database client (Prisma)
  * `api` - Contains the shared API client (Axios)
  * `config-eslint` - Contains the shared ESLint configuration
  * `config-typescript` - Contains the shared TypeScript configuration
  * `payments` - Contains the payment database client (Prisma)

## Deployment

The project is managed using Docker Compose. Simply run the build command to deploy:

```bash
docker compose up
```

Once deployed & up & running, you will need to create & deploy migrations to your database to add the necessary tables. This can be done using [Prisma Migrate](https://www.prisma.io/migrate):

```bash
npx prisma migrate dev
```

If you need to push any existing migrations to the database, you can use either the Prisma db push or the Prisma migrate deploy command(s):

```bash
yarn run db:push

# OR

yarn run db:migrate:deploy
```

There is slight difference between the two commands & [Prisma offers a breakdown on which command is best to use](https://www.prisma.io/docs/concepts/components/prisma-migrate/db-push#choosing-db-push-or-prisma-migrate).

An optional additional step is to seed some initial or fake data to your database using [Prisma's seeding functionality](https://www.prisma.io/docs/guides/database/seed-database).

```bash
yarn run db:seed
```

## Useful Links

Learn more about the power of Turborepo:

* [Tasks](https://turbo.build/repo/docs/core-concepts/monorepos/running-tasks)
* [Caching](https://turbo.build/repo/docs/core-concepts/caching)
* [Remote Caching](https://turbo.build/repo/docs/core-concepts/remote-caching)
* [Filtering](https://turbo.build/repo/docs/core-concepts/monorepos/filtering)
* [Configuration Options](https://turbo.build/repo/docs/reference/configuration)
* [CLI Usage](https://turbo.build/repo/docs/reference/command-line-reference)
