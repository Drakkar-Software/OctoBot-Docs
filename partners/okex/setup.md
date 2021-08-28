# Account setup

An API Key can be considered as a username that is generating to allow access to data.

An API Secret, also referred to as API Private Key is simply a password used in combination with an API Key.

An API Password, also referred to as `Passphrase`, is considered an extra layer of security that is generally user generated. In this instance, you can create an API password to lock the API Key and Secret created on the OKEx website. You will only be able to see your API Key and Secret by inputting the password you selected.

## Create an account on OKEx

- Fill [this OKEx](https://www.okex.com/join/9403477) registration form

## Generate API key

### Generate Your Keys
- Sign into your OKEx account
- Click on your profile in the top right corner.
- Click on the `API`
- Click on `Create V5 API Key`

![OKEx-Create-API-Key](https://raw.githubusercontent.com/Drakkar-Software/OctoBot/assets/docs/OKEx/OKEX-My-Api.png)

### Configure the API Settings
- Give a name to your API Key, and set a Passphrase. 
{% hint style="warning" %}
Make sure to remember that Passphrase, as you will need to use it again in a few moments.
{% endhint %}
- OctoBot needs the `Read` function to be able to pull in balances from OKEx and `Trade` to create new orders.
- Click on Confirm, then click on `View` to see your API Key and API Secret.

![OKEx-Configure-API-Key](https://raw.githubusercontent.com/Drakkar-Software/OctoBot/assets/docs/OKEx/OKEX-Create-v5-key.png)

## Add the API key to OctoBot

### Add OKEx exchange
- Start your OctoBot
- Click on `Accounts` tab
- Click on `Exchanges` on the left menu
- Click on the selector and search `OKEx`
- Click on `ADD`

![OctoBot-Add-Exchange](https://raw.githubusercontent.com/Drakkar-Software/OctoBot/assets/docs/OKEx/OKEx-OctoBot-Add-Exchange.png)

### Add OKEx API keys
- Copy and paste `API Key` from OKEx to OctoBot `API Key` field
- Copy and paste `Secret Key` from OKEx to OctoBot `API Secret` field
- Enter your OKEx `API Password` to OctoBot `API Password` field
![OctoBot-Validate-Credentials](https://raw.githubusercontent.com/Drakkar-Software/OctoBot/assets/docs/OKEx/OKEx-OctoBot-Add-Exchange-Creds.png)
- Click on `Save And restart` `
![OctoBot-Validate-Credentials](https://raw.githubusercontent.com/Drakkar-Software/OctoBot/assets/docs/OKEx/OKEx-Save-And-Restart.png)
