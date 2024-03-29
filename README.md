![Contractorium](https://cdn.discordapp.com/attachments/375333831496040458/1072150670913831003/Screenshot_2023-02-06_at_14.43.41.png)
# Contractorium - The Asset Based Bug Bounty platform.
## What is Contractorium?
Contractorium is a DApp where companies can create a bug bounty program for their product(s) (Which will be stored in a Box storage, mapped to the program managers address). Which in fact lets Ethical Hackers and researchers around the world, browse a wide variety of public bug bounty programs. If they believe, they found a bug, a low-severity vulnerability, they can submit a report, detailing their findings, and if the company decides so, they can get a compensation for their work. Bounties are represented as ASA's, which makes the whole flow much easier to handle, and more transparent.

### What does the project include?
 - A smart contract written in PyTeal with the help of the Beaker framework, and Boxes.
 - A Frontend for the contract written in SvelteKit, and TailwindCSS, with the help of Beaker-TS, and the generated client.

### But how does it actually work?
```mermaid
---
title: Contractorium platform
---
graph TD
    A[Company or Project creates a Bug Bounty program on Contractorium] -->|Optinally go through the verification process, currently it works on a reach out basis| B(The program is now live on the Contractorium platform)
    B --> C{A Bug Bounty hunter or researcher finds the program,\n and start working on it,\n and eventually submit a report.\n which will be shown on their profile. The report is represented as an ASA,\n which acts like an NFT, but the metadata schema differs from the standard.\n The reserve address is the program owner's address,\n the freeze address is the report creator\n and the manager is the program itself.}
    C -->|The hunter decides to close the report| D[On the frontend they issue an application call\n which will destroy the asset representing the bounty program]
    C -->|The program manager decides to compensate the hunter for their findings| E[They issue an application call\n which will pay out the hunter, after subtracting the platform fees, which is currently 2% \n then destroy the asset.]
  
```
## Admin
As of now we have an admin functionality implemented where the contract manager can delete specific programs. (It looks exactly the same way when you delete your program, that's why it wasn't explicitly featured in the video.). But in the future we would like to implement this as a DAO functionality.

## How to setup Contractorium?
First of all, a live instance is deployed on the Testnet, and a frontend app on Vercel which you can find here.. LINK

### Tech stack
 - Contract: `Beaker`
 - FrontEnd: `SvelteKit` and `TailwindCSS` with various SDKs such as `algosdk` and `myalgoconnect`

But, if you decide to set it up here are the steps:
### Contract
Requirements:
 - `poetry`
 - `python 3.10<=`
 

Steps:
- `cd backend`
- `poetry install`
- inside the poetry environment execute the deploy script inside the utils folder, after specifying your algod config (`poetry shell` and then `python deploy.py`)
- That's it. I swear.

### Frontend
- `cd frontend`
- `npm install`
 `npm run dev`


Specify the following env vars:
 - `PUBLIC_ALGOD_SERVER`
 - `PUBLIC_ALGOD_PORT`
 - `PUBLIC_APP_ID`
 - `PUBLIC_ALGOD_TOKEN` (It's public as of now, due to the fact that the public Algonode API does not require a token)
 - `PUBLIC_APP_ADDRESS`
 - `PRIVATE_PINATA_JWT`
 - `PUBLIC_ORIGIN` (It is used for content resolution in my case https://contractorium.vercel.app)
 - `PUBLIC_PINATA_GATEWAY` (the URL to the gateway, if public, then no need for PUBLIC_ORIGIN)
 - `PUBLIC_MANAGER` - The Contract manager, by default the creator.

That'll run a dev server, locally, you'll also need to have a MyAlgo wallet setup.
## ⚠️ Warning! Due to some known issues, you might have to allow the site to open Pop-Ups, it is more than inconvenient, but it's a one time settings adjusting!
# Credits:
- The Design and the majority of the frontend components was made by [@Marci0817](https://github.com/Marci0817)
