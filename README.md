# ERC721
![image](https://github.com/DCVglobalnetwork/ERC721/assets/105791829/dd051534-2897-4e71-981e-fa879092fd35)


![Screenshot 2024-02-23 143804](https://github.com/DCVglobalnetwork/ERC721/assets/105791829/d0179c87-49c3-46e9-8440-0810a2f29dce)



Develop an NFT Smart Contract (ERC721) 
using 
* Alchemy
  https://www.alchemy.com/
* OpenZeppelin
  https://wizard.openzeppelin.com/#erc721
* Remix
  https://remix.ethereum.org/
* Ethereum Sepolia
  https://sepolia.etherscan.io/

## Get free Sepolia ETH using https://sepoliafaucet.com/

use the OpenZeppelin Wizard to create the smart contract
![web3](https://github.com/DCVglobalnetwork/ERC721/assets/105791829/e3396c5b-b9e0-4f97-92d4-565944cbcf5d)

for more read the documentations on openzeppelin
writing smart contracts, security is key
OpenZeppelin serves this purpose
use any name for your token and symbol
As you can see above these are the Token Features
Mintable will create a mint function only callable by privileged accounts
Autoincrement IDs will automatically assign incremental IDs to your NFTs
Enumerable will give you access to on-chain Tokens enumeration and functions such as “totalSupply”, not present in the default ERC721 integration URI storage, to associate metadata and images to each of your NFTs
URI Storage to be able to associate URIs to our NFTs

***learn more about these modules, check the official OpenZeppelin documentation about the ERC721 standard.***

as you might have noticed, on top of the OpenZeppelin Wizard editor, there’s the button “Open in Remix"

Clicking on it will open REMIX IDE in a new browser tab.

Using Remix to modify an NFT smart contract

we import some libraries and initialize the smart contract.
![web3g](https://github.com/DCVglobalnetwork/ERC721/assets/105791829/a4bb73d2-0f5e-4c91-b411-5c11e736650e)

* remove it from the contract declaration "Ownable", and the library imports

```javascript
import "@openzeppelin/contracts/access/Ownable.sol";
```
* everyone will be able to mint our NFTs, you'll need to avoid people from minting more NFTs than the max number of NFTs in our collection. To do so let's specify the max number of mintable NFTs.

* the users want to be able to mint up to a total of 10,000 NFTs.
* create a new uint256 variable, call it MAX_SUPPLY, assign it 10,000.
```javascript
Counters.Counter private _tokenIdCounter;
    uint256 MAX_SUPPLY = 100000;

    constructor() ERC721("QuantaVastitude", "QVT") {}
```
* move into the safeMint function and add a require statement:
```javascript
  require(_tokenIdCounter.current() <= MAX_SUPPLY, "I'm sorry we reached the cap");
```
* create a free account on Alchemy.com
* add it as a node provider on Metamask
* get some free Sepolia ETH

  
Alchemy
Select the Ethereum
choose the Sepolia network and click on create App
you should get this 
![n](https://github.com/DCVglobalnetwork/ERC721/assets/105791829/9011fa8e-6fb3-4668-93ac-f942f292f4b3)

# Get your Key

![j](https://github.com/DCVglobalnetwork/ERC721/assets/105791829/d742f96c-29bd-4c5a-a085-bb5fac37e230)

click on the “VIEW KEY” button on the top right corner and copy the HTTP URL

***Add Alchemy Sepolia to Your Metamask Wallet***


Add the following information to the form:

Network name: Alchemy Sepolia

New RPC URL: the HTTP URL of the Sepolia Alchemy Application

Chain ID: 11155111

Currency Symbol: Sepolia ETH

Block Explorer: https://sepolia.etherscan.io/

![Screenshot 2024-02-23 141650](https://github.com/DCVglobalnetwork/ERC721/assets/105791829/d5d304d5-e422-4642-9ad3-8e7fc3f5a6ed)

Free Sepolia Test ETH

![Screenshot 2024-02-23 142258](https://github.com/DCVglobalnetwork/ERC721/assets/105791829/e684b27e-6539-4361-adb9-0a4578304485)

## Now back to Remix
* click on the compiler menu on the left-hand side of the page 
* click on The blue “Compile” button
* the Metamask wallet is on the Alchemy Sepolia network
* select the NFT Smart contract from the Contract dropdown menu
* click on Deploy

A Metamask pop-up window will appear, click on "sign" and proceed to pay the gas fees.

If everything worked as expected, after 10 seconds you should see the contract listed under Deployed Contracts:
![df](https://github.com/DCVglobalnetwork/ERC721/assets/105791829/944a47bf-ec30-4109-ab77-8158fe82f1e2)

## NFTs Metadata
You can read more about metadata standards on the official OpenSea documentation

## create and upload the metadata on IPFS
the contract will need to return a URI pointing to the hosted metadata. To find this URI

OpenSea, Rarible and other popular marketplaces will use the tokenURI method contained in the ERC721Uristorage standard

https://docs.opensea.io/docs/metadata-standards

![Screenshot 2024-02-23 144549](https://github.com/DCVglobalnetwork/ERC721/assets/105791829/cdd297af-bdf5-4403-96cd-44f2bbab1dd7)

attributes

![Screenshot 2024-02-23 144613](https://github.com/DCVglobalnetwork/ERC721/assets/105791829/81f3ef6e-6fd7-4732-a7fd-d038bec86746)


Format Your NFT Metadata

```javascript

{ 
  "description": "YOUR DESCRIPTION",
  "external_url": "YOUR URL",
  "image": "IMAGE URL",
  "name": "TITLE", 
  "attributes": [
    {
      "trait_type": "Base", 
      "value": "Starfish"
    }, 
    {
      "trait_type": "Eyes", 
      "value": "Big"
    }, 
    {
      "trait_type": "Mouth", 
      "value": "Surprised"
    }, 
    {
      "trait_type": "Level", 
      "value": 5
    }, 
    {
      "trait_type": "Stamina", 
      "value": 1.4
    }, 
    {
      "trait_type": "Personality", 
      "value": "Sad"
    }, 
    {
      "display_type": "boost_number", 
      "trait_type": "Aqua Power", 
      "value": 40
    }, 
    {
      "display_type": "boost_percentage", 
      "trait_type": "Stamina Increase", 
      "value": 10
    }, 
    {
      "display_type": "number", 
      "trait_type": "Generation", 
      "value": 2
    }]
  }
```
## Go on JSON EDITOR ONLINE

paste all the metadata you have chosen from above 

![Screenshot 2024-02-13 000832](https://github.com/DCVglobalnetwork/ERC721/assets/105791829/67d9f63e-9264-4785-acaf-4b420e668519)

Modify and change the name and symbol of the token for your token, see example below

![Screenshot 2024-02-13 124028](https://github.com/DCVglobalnetwork/ERC721/assets/105791829/d9a4364a-78be-48f7-aa2d-a7a1262f9c51)


## create it and store it on IPFS

* go to filebase.com and create a new account

![Screenshot 2024-02-13 111342](https://github.com/DCVglobalnetwork/ERC721/assets/105791829/b7dd9c35-e6df-4265-8c3a-411c6a4c66c6)

* logged in
* click on the bucket button on the left-hand side menu
* create a new bucket

![Screenshot 2024-02-14 122535](https://github.com/DCVglobalnetwork/ERC721/assets/105791829/b543eead-df9b-493c-98af-bab23939cd15)

* go into the bucket
* click on the upload button
* upload the image you want to use for your NFT
* Once uploaded click on it and copy the IPFS Gateway URL
  
![Screenshot 2024-02-13 124328](https://github.com/DCVglobalnetwork/ERC721/assets/105791829/d3d50739-9690-42e0-bbf1-bc2ce5a13fbe)

##  paste the following JSON code 

* once you're done, save it

![Screenshot 2024-02-13 124122](https://github.com/DCVglobalnetwork/ERC721/assets/105791829/ab3196e8-780e-4a85-9fb7-5ea7c478ef5a)

* go to Filebase and upload the metadata.json file in the same bucket where we uploaded the Image.

* click on the CID and copy it we’ll need it in the next part to build the token URI when minting out NFT

* back to Remix and in the Deploy & Run Transactions menu, go under “deployed contracts”
* click on the contract we just deployed
* it will open up a list of all the methods contained in your Smart contact
* 
Orange methods are methods that actually write on the blockchain whereas Blue methods are methods learning from the blockchain.

Click on the safeMint method dropdown icon and paste your address and the following string into the uri field

![Screenshot 2024-02-13 124601](https://github.com/DCVglobalnetwork/ERC721/assets/105791829/921021af-7854-4aa3-9fa9-7225ddbdeb40)

![Screenshot 2024-02-13 124740](https://github.com/DCVglobalnetwork/ERC721/assets/105791829/46bcdbbc-d055-4941-bb36-52ccff0241f7)


![Screenshot 2024-02-13 124714](https://github.com/DCVglobalnetwork/ERC721/assets/105791829/4c0c9075-ac7a-4f3a-a357-a876343e393f)

* clicking on transact will create a Metamask popup prompting you to pay the gas fees
  
![Screenshot 2024-02-13 124809](https://github.com/DCVglobalnetwork/ERC721/assets/105791829/a459ac8f-1c2a-45d1-8d96-7629d3e1f90f)

* click on "sign" and go on minting your first NFT!

* copy and paste your address in the balanceOf method input, and run it - it should show you have 1 NFT

![Screenshot 2024-02-14 123429](https://github.com/DCVglobalnetwork/ERC721/assets/105791829/f387797f-71b9-44e4-8b45-1843dae5d23a)


Do the same with the tokenUri method, inserting “0” as the id argument - it should display your tokenURI.

Great! You just minted your first NFT! 

Sepolia testnet 

![Screenshot 2024-02-13 124907](https://github.com/DCVglobalnetwork/ERC721/assets/105791829/dd63b0b2-dabc-4145-8448-a8540d4f18fb)


## move to OpenSea to check if the metadata begins to read

* go to testnets.opensea.io
* log in with your Metamask wallet
* click on your profile picture
* you should see your newly minted NFT there
* If the image is not yet visible
* click on it
* click on the “refresh metadata” button

![Screenshot 2024-02-14 122757](https://github.com/DCVglobalnetwork/ERC721/assets/105791829/3033c9fb-5706-454f-a492-7beb58ee85a6)

HAPPY CODING!!!
Thank you 
 








