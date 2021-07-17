# Tests

## Requirements

To run OctoBot's tests, an OctoBot development environment is necessary, development environment setup is described [here](https://github.com/Drakkar-Software/OctoBot-Docs/tree/624bac35cfdd4b92e96356538d28ac0e39d983d3/Coding/Developer-Guide.html#environment-setup)

## OctoBot engine

To run OctoBot's engine tests, use the _pytest tests_ in OctoBot's root folder :

```bash
pytest tests
```

This will run all tests in the test folder.

## Tentacles

To run OctoBot's tentacles tests, use the _pytest tentacles_ command in OctoBot's root folder :

```bash
pytest tentacles
```

This will run all tests in the **tentacles** folder. Testing tentacles works only if tentacles are installed on the tested OctoBot. See [OctoBot's tentacle manager](https://github.com/Drakkar-Software/OctoBot-Docs/tree/624bac35cfdd4b92e96356538d28ac0e39d983d3/Coding/Tentacle-Manager.html) to install tentacles.

