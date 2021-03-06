---
layout: post
title:  Eos deployer
tags:
- News
- Tags
- Blog
- Post
---
##### Repository

[https://github.com/yashwanth2804/EOSdplyr](https://busy.org/exit?url=https%3A%2F%2Fgithub.com%2Fyashwanth2804%2FEOSdplyr)

#### What is EOSdplyr

_cleos is a command line interface which used to interact with blockchain_

Being an entry level developer in EOS,it is hard for me to manage multiple terminal windows opened ,its a very time consuming process,confusing.This EOSdplyr aims to speed-up the development process by simple GUI action from web ,which intern executes the normal bash actions.

#### Prerequisites

Please follow the [Develpoers docs](https://busy.org/exit?url=https%3A%2F%2Fdevelopers.eos.io%2Feosio-home%2Fdocs)

make sure 

cloes command executes after you run the docker image .

> Note your 

CONTRACTS_DIR folder absolute path,

development keyand 

wallet key.[provide these to .env file in project folder]

#### Targeted developers

This is targeted for the entry level developers in EOS platform,It is suggested to have development environment setup with CLION or alternative as you mature.

#### Install && Setup

Clone the repo  

```
git clone https://github.com/yashwanth2804/EOSdplyr.git  
  

cd Eosdplyr  
  

npm install  
  

npm start  

```  
  
Change 

.env file configurations   
  

Walletkey, your wallet imported private key.   
  

path, absolute path for the contract folder. (should ends with forwardslash 

/ )  
  

Development key , this is the key which used to create accounts.  
  
  

> make sure you don't expose keys in deployment environment

now open the browser 

http://localhost:3001/  
  

> Run 

docker start eosio if you have't started docker service

#### Features

##### Create Account

<img src="https://steemitimages.com/0x0/https://cdn.steemitimages.com/DQmRV2dkmWY53cj9qdUZK1Q6qdvUcYWVzDN6FYkxN1JvDUi/Deployment-ca.png" alt="drawing" width="750rem" height="350rem"/>
 

 
This snippet will create the account with the name given by you.

##### Create Contract Account

This snippet will create the contract account and generates the folder with provided contract name and cpp file with basic template of 

hellosmartcontract.

> 

CONTRACTS_DIR/ContractName/ContractName.cpp

#### Compile & Set Contract

This snippet will compile the cpp file and generates the 

wasm and 

abifiles,

after the compilation this will be pushed to blockchain using 

set contract

* * *

#### Push Action



<img src="https://steemitimages.com/0x0/https://cdn.steemitimages.com/DQmPZ4wtsqY3AvcDi8TQR8exsaiyFUtsctch5pAEeJ9EV8w/push-action.png" alt="drawing" width="750rem" height="350rem"/>

 

* * *

#### Get Table

<img src="https://steemitimages.com/0x0/https://cdn.steemitimages.com/DQmWP5iq3ohQmp4Jyj9HCDR7a3pxue2XmeUB5DK8rCpuj51/table.png" alt="drawing" width="750rem" height="350rem"/>
 
This snippet will gets the table from smart contract.

* * *

### Tech Stack

Node,express,Html,Css,Bash script

### How to contribute?

- Fork it [[https://github.com/yashwanth2804/EOSdplyr](https://busy.org/exit?url=https%3A%2F%2Fgithub.com%2Fyashwanth2804%2FEOSdplyr)] 
- Clone it [[https://github.com/&lt;your_github_name](https://busy.org/exit?url=https%3A%2F%2Fgithub.com%2F%3Cyour_github_name)&gt;/EOSdplyr.git or git@github.com:your_github_name/EOSdplyr.git] 
    - git clone [https://github.com/your_github_name/EOSdplyr.git](https://busy.org/exit?url=https%3A%2F%2Fgithub.com%2Fyour_github_name%2FEOSdplyr.git)

- Create a branch 
    - cd first-contributions 
    - git checkout -b 

- Add features 
    - git add you_worked_files 
    - git commit -m "what your features" 

- push it 
    - git push origin your_branch 
    - Submit a pull request 

##### GitHub Account

[https://github.com/yashwanth2804](https://busy.org/exit?url=https%3A%2F%2Fgithub.com%2Fyashwanth2804)
