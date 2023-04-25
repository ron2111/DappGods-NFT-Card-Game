## Web3 setup

0. `cd web3`
1. `npx hardhat` -> y → typescript → enter → enter
2. `npm install @openzeppelin/contracts dotenv @nomiclabs/hardhat-ethers` + Hardhat packages `npm install --save-dev "hardhat@^2.12.0" "@nomicfoundation/hardhat-toolbox@^2.0.0"`
3. Install [Core](https://chrome.google.com/webstore/detail/core/agoakfejjabomempkjlepdflaleeobhb), a Metamask smart wallet alternative built for Avalanche dApps
4. Turn on the testnet mode by: opening up the Core extension -> click the hamburger menu on the top left -> go to advanced -> turn on the testnet mode
5. Fund your wallet from the [Avax Faucet](https://faucet.avax.network/)
6. Create a `.env` file and specify a PRIVATE_KEY variable.
7. To get to the private key, do the following steps:
8. Open up the Core extension -> click the hamburger menu on the top left -> go to security and privacy -> click show recovery phase -> enter your password -> copy the phrase -> go to [wallet.avax.network](https://wallet.avax.network/) -> click access wallet -> choose mnemonic key phrase -> paste what the words we’ve copied from Core -> on the sidebar click manage keys -> view c-chain private key -> copy -> paste it in the .env file
9. Copy the `hardhat.config.ts` file from the GitHub gist down in the description
10. Copy the `deploy.ts` script from the GitHub gist down in the description
11. Copy the `AvaxGods.sol` smart contract code from the GitHub gist down in the description
12. Compile the contract by running the `npx hardhat compile` command
13. Deploy the smart contract on the Fuji test network by running the `npx hardhat run scripts/deploy.ts --network fuji` command
    Move the `/artifacts/contracts/AVAXGods.json` file to the `/contract` folder on the frontend
    Copy the address of the deployed contract from the terminal and paste it into the `/contract/index.js` file of the frontend application

## Client Code:

- `src/assets` contains all the backgrounds, sounds and card images required for the game. For ex: explosion sounds, player logo image etc.
- `components` contain an `OnboardModal.jsx` file that is a web3 - client side checks component that ensures that the wallet is connected properly or if you have enough Avax tokens in the wallet. It also checks that we are on the correct chain.
- `utils` has the `onboard.js` & `animation.js` files.
  onboard.js helps in powering up the `OnboardModal.jsx` modal.
  animation.js helps in getting the 8-bit animation which will be used in the game (taken from codepen) when the player's cards are attacked.

For styles there is an index.js file that contains tailwind styles.

- Higher Order Components
  `PageHOC.jsx`: Page Higher Order Component FILE
  Its sort of a wrapper and all other components are displayed within it.

-Same as Home.jsx, Create Battle page is also wrapped by PageHOC with different title and description props

-Created an `index.js` file to handle he import/exports from `page` folder

-Now created a `context` folder in `src`, which will help in connecting smart contract to react.
-as we have wrapped the Global Context Provider around Home and other components, we can use its context in them.

- Core injects web3 functionalities right into the browser

- Made a `contract` folder which has `index.js`and `AvaxGods.json` taken from `web3/artifacts`. Then export he abi for the contract - client interaction.

- At this stage, we are able to open the wallet for approval, this means we are now able to connect the wallet with our smart contract.

- the `updateCurrentWalletAddress` method which asks for ethAccount is now able to ask for it through the wallet.

- Made a `CustomInput` & `CustomButton` folder in components. These will act as reusable components for inputs and buttons like the input area and the `Register` button on the homepage.

- In `Home.jsx`'s CustomInput, no special character or char outside the regex: `/^[A-Za-z0-9]+$/` can't be entered.This is checked by the onChange event
