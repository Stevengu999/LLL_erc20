# LLL

According to the [Homestead Documentation](http://www.ethdocs.org/en/latest/contracts-and-transactions/contracts.html#id4),

> Lisp Like Language (LLL) is a low level language similar to Assembly. It is meant to be very simple and minimalistic; essentially just a tiny wrapper over coding in EVM directly.

LLL is one of the three living languages for Ethereum contract creation, alongside Solidity and Serpent (which itself compiles to LLL). If you have the Solidity compiler, then you have LLL! It's bundled with `solc` as `lllc`.

It's fair to say that LLL is lagging far, far behind Solidity in popularity for contract creation. But, Daniel Ellison of Consensys is on a [crusade](https://media.consensys.net/@zigguratt) to revive it. [Here](http://blog.syrinx.net/the-resurrection-of-lll-part-1/) as well.

LLL is a low-level language, just one step above Ethereum Virtual Machine (EVM) bytecode.  Why would we choose to go back to the 1970s in programming terms when we have all the object-oriented joys of Solidity at our disposal?

Well, the EVM is a severely resource-constrained environment. Execution, memory and storage all have significant costs. For all its popularity, the Solidity compiler is not great at producing very efficient code. The bytecode generated by Solidity is full of redundancies, bloat, pointless jumps and other inefficiencies that cause steam come out of my ears, but, much more importantly, unnecessarily high gas usage.

The low-level nature of LLL reminds you constantly that you are dealing with a resource-constrained environment. The LLL compiler doesn't auto-generate any of the junk you see in Solidity bytecode. This typically results in LLL bytecode being substantially more compact and efficient to run than Solidity bytecode.  It is for this reason that the [deployed ENS registry](https://etherscan.io/address/0x314159265dd8dbb310642f98f50c066173c1259b#code) was [written in LLL](https://github.com/ethereum/ens/blob/master/contracts/ENS.lll).

Of course, there are downsides. High-level languages exist for a reason. But it's not as bad as you might imagine. After only a week's spare time dabbling with LLL I was able to code up the `erc20.lll` example here. And I'm not any kind of developer by profession (which may be apparent from the code!).

## *erc20.lll*: An implementation of Ethereum ERC20 tokens in LLL

A fully functional (but as yet not fully tested) implementation of the [ERC20 token standard](https://theethereum.wiki/w/index.php/ERC20_Token_Standard).
