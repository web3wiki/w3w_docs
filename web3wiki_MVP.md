# web3wiki(w3w) MVP

## Page structure

web3wiki is composed of separate **project pages**, each of which is composed of multiple **sections**. All  Sections are same in all w3w pages, and one page cannot have two sections with the same name. The reasoning behind this is, so that different frontends can show only specific sections for specific project pages, or show only one section for all existing project pages. 

## Landing page 
To be decided 

section 1
list of newest / most popular w3w pages

section 2
search button
searches for specific w3w pages
-> calls wikiPageMapping("query"(e.g. "cryptopunks") -> array(array containing all crypotpunk sections))
    

## Project page 

- every project page has an array associated with it, it contains all section pointers for specific page

to load a page: 
1. FE must get from registryContract which pageArray it must call to get the page content 
2. FE must go through all items of the array, these contain pointers to a specific NFT(content is stored as NFT) . 3. FE must then fetch and display these NFTs 


# Actions 

## Updating a project page 

*every page is divided into sections, sections are atomic, every time a maintainer wants to update content, he mints a new nft and updates smart contract registry*

to update a page: 
1. FE needs to ask maintainer to connect a wallet, it checks if connected wallet is the maintainer for each section. For the section that the wallet is the maintainer for, it will show edit button.
2. Once a maintainer clicks `edit` he can write in / upload new content for the section, then he hits `mint`. This action will work with NFT.storage component. This component will generate CID(pointer pointing to IPFS content) upload the content to IPFS. 
3. the button next to content will change to 'update'. Now maintainer will send a transaction to update the registry. This will generate tx, that will change an array item associated with this section, to update the pointer to the new NFT.

# Functionality needed

## backend
owner: Marko
1. registryContract -> contrant containing structure of all wiki pages, their sections and pointers to them

## frontend 

### displaying project page
owner: ?Nico
1. Fetching pointers to a specific project page based on project page name.
2. Digesting these pointers, figuring out which NFTs need to be rendered. then displaying NFTs(sections)

### editing project page 
owner: ?Ashish
Everything described in the *Updating a project page* section


# Application ideas 

This structure could be really powerfull + modular, go beyond creating interesting content.

* People could create new novel wikipages, by combining existing regular NFTs, sections they create, section from other wiki pages. 
* There could be wiki pages that just record history of one wiki other. 
* **every entry and edit turns into NFT**, these could be traded, sold split or done whatever. 
