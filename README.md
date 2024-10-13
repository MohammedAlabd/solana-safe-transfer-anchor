# Solana Safe Transfer Anchor

An anchor program that requires a confirmation code in addition to the wallet address before transferring tokens.

## Instructions

### Initialize Confirmation Account

This method initializes the confirmation account with a random confirmation code.

It takes no arguments. And the Accounts that it needs are:

- `signer`: The account that the confirmation code will get generated to.
- `system_program`: The system program account.
- `confirmation_account`: The confirmation account PDA.

### Transfer SOL

This method transfers SOL from one account to another.

It takes two arguments:

- `amount`: The amount of SOL to transfer.
- `confirmation_code`: The confirmation code.

The Accounts that it needs are:

- `from`: The account that the SOL will be transferred from.
- `to`: The account that the SOL will be transferred to.
- `system_program`: The system program account.
- `confirmation_account`: The confirmation account PDA.

### Transfer SPL Tokens

This method transfers SPL tokens from one account to another.

It takes two arguments:

- `amount`: The amount of SPL tokens to transfer.
- `confirmation_code`: The confirmation code.

The Accounts that it needs are:

- `token_program`: The token program account.
- `system_program`: The system program account.
- `associated_token_program`: The associated token program account.
- `mint`: The mint account.
- `from_token_account`: The account that the SPL tokens will be transferred from.
- `from_authority`: The authority account of the `from_token_account`.
- `to_token_account`: The account that the SPL tokens will be transferred to.
- `to_authority`: The authority account of the `to_token_account`.
- `confirmation_account`: The confirmation account PDA.

## How to test it

- Install dependencies

```bash
bun install
```

- Update the prgoram key

```bash
anchor keys sync
```

- Run the test

```bash
anchor test
```

This will build the program, spin up a local validator, and run the tests.
The tests will make sure that the three instructions are working as expected.

## How to deploy it

- Update the program key

```bash
anchor keys sync
```

- build the program

```bash
anchor build
```

- run a local validator

```bash
solana-test-validator
```

- Deploy the program

```bash
anchor deploy
```
