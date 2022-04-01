---
layout: post
title:  "Welcome to Jekyll!"
date:   2022-04-01 15:32:52 +0800
categories: jekyll update
---


> 本教程将教会你如何成为一个NFT创建人并如何构建一个基于React的全栈dApp来连接您的智能合约和MetaMask钱包以及相关Web3工具。

从过完经验来看，对于一个传统的前端工程师来说构建一个前端应用并非难事，但是如何让应用于智能合约进行交互则是一个首要跨过的门槛。在本项目中您将学会：

1. 如何将您的前端项目与智能合约进行连接；
2. 如何在前端应用中调用智能合约的方法；
3. 使用MetaMask钱包对交易进行签名。

> 本项目将基于React前端框架，所以我们会假定开发者是一个熟悉React前端框架的成熟开发人员。

话不多说，我们开始接下来的教程。在了解代码之前，开发人员需要了解NFT的底层是什么。就狭义上的以太坊NFT而言，它底层实际上是基于ERC-721和ERC-1155两个标准的智能合约。这两个标准的区别在于ERC-721一次只能传输单一NFT资产，而ERC-1155则可以进行批量传输。而我们通俗意义上讲的“NFT数字资产”则是通过调用智能合约里的Minting function所生成的实例（instance），该实例运行在区块链上并具有唯一性。



## 连接MetaMask

在src文件中创建一个utils文件夹，并在里面创建一个interact.js文件，这个文件中我们将编写connectWallet函数，之后我们会在Minter.js组件中对其进行调用。

```js
export const connectWallet = async ()=>{
    if(window.etherum){
      try{
        // 在这里我们调用的是Metamask插件的全局API
        const addressArray = await window.etherum.request({
            method:"eth_requestAccouts"
        });
        return {
            address:addressArray[0],
            status:"MetaMask链接成功"
        }
      }catch(e){
       return {address:"",status:e.message}
      }
    }else{
        return {
            address:"",
            status:"请使用Chrome浏览器并安装MetaMask插件"
        }
    }
}
```

现在我们看下React前端代码：

```js

```