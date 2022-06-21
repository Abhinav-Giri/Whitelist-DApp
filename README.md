# Whitelist-DApp

We are launching our NFT collection named `Crypto Devs`. We want to give our early supporters access to a whitelist for our collection, so here we are creating a whitelist dapp for `Crypto Devs`

![](https://i.imgur.com/zgY0TGo.png)

## Requirements

- Whitelist access should be given to the first `10` users for free who want to get in.
Lets start building 🚀

---

## Build

### Smart Contract

To build the smart contract we will be using [Hardhat](https://hardhat.org/).
Hardhat is an Ethereum development environment and framework designed for full stack development in Solidity. In simple words we can write our smart contract, deploy them, run tests, and debug our code.



 - First, we need to create a `Whitelist-DApp` folder where the Hardhat project and our Next.js app will later go
 - Open up a terminal and execute these commands
  ```bash
  mkdir Whitelist-DApp
  cd Whitelist-DApp
  ```
 - Then, in Whitelist-Daap folder, we will set up Hardhat project 
  ```bash
  mkdir hardhat-n
  cd hardhat-n
  npm init --yes 
  or 
  yarn init --yes
  npm install --save-dev hardhat 
  or
  yarn add hardhat --dev
  ```

- In the same directory where we installed Hardhat run:

  ```bash
  npx hardhat
  ```

  - Select `Create a basic sample project`
  - Press enter for the already specified `Hardhat Project root`
  - Press enter for the question on if you want to add a `.gitignore`
  - Press enter for `Do you want to install this sample project's dependencies with npm (@nomiclabs/hardhat-waffle ethereum-waffle chai @nomiclabs/hardhat-ethers ethers)?`

Now we have a hardhat-n project ready to go!

If we are not on mac, please do this extra step and install these libraries as well :)

```bash
npm install --save-dev @nomiclabs/hardhat-waffle ethereum-waffle chai @nomiclabs/hardhat-ethers ethers
or
yarn add @nomiclabs/hardhat-waffle ethereum-waffle chai @nomiclabs/hardhat-ethers ethers --dev
```

- Start by creating a new file inside the `contracts` directory called `Whitelist.sol` as shown above... in the repo.

- Lets deploy the contract to `rinkeby` or anyother network of our choice.Create a new file named `deploy.js` under the `scripts` folder

- Now we will write some code to deploy the contract in `deploy.js` file as shown above... in the repo.

- Now create a `.env` file in the `hardhat-n` folder and add the following lines, use the instructions in the comments to get the Alchemy API Key URL and RINKEBY Private Key. Make sure that the account from which we get our rinkeby private key is funded with Rinkeby Ether as shown above... in the repo.

- Now we will install `dotenv` package to be able to import the env file and use it in our config. Open up a terminal pointing at `hardhat-n` directory and execute this command
  ```bash
  npm install dotenv
  or 
  yarn add dotenv
  ```
- Now open the hardhat.config.js file, we would add the `rinkeby` network here so that we can deploy our contract to rinkeby. Replace all the lines in the `hardhar.config.js` file as shown above... in the repo.

- Compile the contract, open up a terminal pointing at `hardhat-n` directory and execute this command

  ```bash
     npx hardhat compile
  ```
  
- To deploy, open up a terminal pointing at `hardhat-n` directory and execute this command
  ```bash
  npx hardhat run scripts/deploy.js --network rinkeby
  ```
- Save the Whitelist Contract Address that was printed on our terminal in the notepad, we would need it later.

### Website

- To develop the website we will use [React](https://reactjs.org/) and [Next Js](https://nextjs.org/). React is a javascript framework used to make websites and Next.js is a React framework that also allows writing backend APIs code along with the frontend, so we don't need two separate frontend and backend services.
- First, we will need to create a new `next` app and our folder structure should look something like

  ```
  - Whitelist-DApp
      - hardhat-n
      - my-app
  ```

- To create this `my-app`, in the terminal point to Whitelist-DApp folder and type

  ```bash
  npx create-next-app@latest
  ```

  and press `enter` for all the questions

- Now to run the app, execute these commands in the terminal

  ```
  cd my-app
  npm run dev
  or 
  yarn dev
  ```

- Now go to `http://localhost:3000`, our app should be running 🤘

- Now lets install [Web3Modal library](https://github.com/Web3Modal/web3modal). Web3Modal is an easy to use library to help developers easily allow their users to connect to their dApps with all sorts of different wallets. By default Web3Modal Library supports injected providers like (Metamask, Dapper, Gnosis Safe, Frame, Web3 Browsers, etc) and WalletConnect, We can also easily configure the library to support Portis, Fortmatic, Squarelink, Torus, Authereum, D'CENT Wallet and Arkane.
  Open up a terminal pointing at`my-app` directory and execute this command

  ```bash
  npm install web3modal
  or
  yarn add web3modal
  ```

- In the same terminal also install `ethers.js`

  ```bash
  npm install ethers
  or 
  yarn add ethers
  ```

- In our my-app/public folder, download `crypto-devs.svg` from the above repo.
- Now go to styles folder and replace all the contents of `Home.modules.css` file with the code shown in the above repo.

- Open the index.js file under the pages folder and paste the code from the above repo.

- Now create a new folder under the my-app folder and name it `constants`.
- In the constants folder create a file, `index.js` use the above repo code.
- Enter your `WHITELIST_CONTRACT_ADDRESS` at the given variable... 
- Enter `abi` with the ABI of your Whitelist Contract. To get the ABI for your contract, go to your `hardhat-n/artifacts/contracts/Whitelist.sol` folder and from your `Whitelist.json` file get the array marked under the `"abi"` key (it will be. a huge array, close to 100 lines if not more).

- Now in your terminal which is pointing to `my-app` folder, execute

  ```bash
  npm run dev
  or
  yarn dev
  ```

Our whitelist dapp should now work without errors 🚀

### Push to github

Make sure before proceeding you have [pushed all your code to github](https://medium.com/hackernoon/a-gentle-introduction-to-git-and-github-the-eli5-way-43f0aa64f2e4) :)

---

## Deploying our dApp

We will now deploy our dApp, so that everyone can see our website.

- Go to [Vercel](https://vercel.com/) and sign in with your GitHub
- Then click on `New Project` button and then select your `Whitelist-DApp repo`
- ![](https://i.imgur.com/ZRjfkCE.png)
- Select the Framework as `Next.js`
- When configuring our new project, Vercel will allow us to customize our `Root Directory`
- Click `Edit` next to `Root Directory` and set it to `my-app`
- Click `Deploy`
- Now we can see our deployed website by going to our dashboard, selecting our project, and copying the URL from there!


You can check my live website here:- [Whitelist-DApp](https://whitelist-dapp-abhinav-giri.vercel.app/)

Special thanks to team@LearnWeb3DAO