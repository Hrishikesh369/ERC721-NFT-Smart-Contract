# ERC721 - NFT

A NFT solidity smart contract built on Foundry development framework where NFT metadata is stored in IPFS.

## Overview 

This ERC721 NFT Smart contract is a collection of "Dogie" NFT's, this contract inherits functions from "OpenZeppelin's" ERC721 standard, ```mintNFT()``` allows anyone to mint their NFT on Sepolia testnet, after minting the tokenId and tokenUri get stored in the mapping, which can be checked using ```tokenURI()```.

## NFT's in "Dogie" Collection


![**Pug**](img/pug.png)

![**St.Bernard**](img/st-bernard.png)

## Functionality

**```constructor() ERC721("Dogie", "DOG")```**

- Initializes the ERC-721 base with name ```"Dogie"``` and symbol ```"DOG"``` and sets ```s_tokenCounter``` to 0.

**```function mintNft(string memory tokenUri) public```**

- Mints a new NFT to ```msg.sender```: stores ```tokenUri``` in ```s_tokenIdToUri``` at the current ```s_tokenCounter```, calls ```_safeMint(msg.sender, s_tokenCounter)```, then increments ```s_tokenCounter```.

**```function tokenURI(uint256 tokenId) public view override returns (string memory)```**

- Returns the URI stored in ```s_tokenIdToUri[tokenId]```. (This override returns the mapping value directly rather than using the ERC721 ```_baseURI()``` concatenation.)

**```function supportsInterface(bytes4 interfaceId) public view virtual override returns (bool)```**

- Standard ERC-165 check; returns ```true``` if ```interfaceId``` matches ERC-721 or ERC-721 Metadata (or a parent).

**```function balanceOf(address owner) public view virtual returns (uint256)```**

- Returns how many tokens ```owner``` holds; reverts if ```owner``` is the zero address.

**```function ownerOf(uint256 tokenId) public view virtual returns (address)```**

- Returns token owner; delegates to ```_requireOwned(tokenId)``` (reverts if nonexistent).

**```function name() public view virtual returns (string memory)```**

- Returns token collection name.

**```function symbol() public view virtual returns (string memory)```**

- Returns token collection symbol.

**```function tokenURI(uint256 tokenId) public view virtual returns (string memory)```**

- Returns metadata URI: requires token exists, then returns ```baseURI + tokenId``` if base is non-empty, otherwise empty string. Can be overridden.

**```function approve(address to, uint256 tokenId) public virtual```**

- Public API to set single-token approval (calls internal ```_approve``` with ```msg.sender``` as auth).

**```function getApproved(uint256 tokenId) public view virtual returns (address)```**

- Returns approved address for ```tokenId``` (reverts if token doesn't exist).

**```function setApprovalForAll(address operator, bool approved) public virtual```**

- Approve/ revoke ```operator``` to manage all caller tokens (emits ```ApprovalForAll```).

**```function isApprovedForAll(address owner, address operator) public view virtual returns (bool)```**

- Returns whether ```operator``` is approved to manage all tokens of ```owner```.

**```function transferFrom(address from, address to, uint256 tokenId) public virtual```**

- Transfers ```tokenId``` from ```from``` to ```to``` after authorization checks; reverts on bad owner or zero to. Uses ```_update``` which enforces approvals/ownership.

**```function safeTransferFrom(address from, address to, uint256 tokenId) public```**

- Safe transfer wrapper calling the ```data``` variant with empty bytes.

**```function safeTransferFrom(address from, address to, uint256 tokenId, bytes memory data) public virtual```**

- Calls ```transferFrom(...)``` then checks ```to``` (if contract) implements ```onERC721Received```.

## Interact 

Interact with "BasicNFT" smart contract deployed on Sepolia through Etherscan - 

https://sepolia.etherscan.io/address/0x29B4F021D74236d9f2fA0F95DF8d752abA9A5730#code

