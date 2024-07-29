/*
       REQUIREMENTS
    1. Your contract will have public variables that store the details about your coin (Token Name, Token Abbrv., Total Supply)
    2. Your contract will have a mapping of addresses to balances (address => uint)
    3. You will have a mint function that takes two parameters: an address and a value. 
       The function then increases the total supply by that number and increases the balance 
       of the address by that amount.
    4. Your contract will have a burn function, which works the opposite of the mint function, as it will destroy tokens. 
       It will take an address and value just like the mint functions. It will then deduct the value from the total supply 
       and from the balance of the address.
    5. Lastly, your burn function should have conditionals to make sure the balance of the account is greater than or equal 
       to the amount that is supposed to be burned.
*/
// SPDX-License-Identifier: MIT
pragma solidity 0.8.18;
contract MyToken {

    // public variables here
    string public tokenName;
    string public tokenAbbrv;
    uint256 public totalSupply = 0;

    // mapping variable here
    mapping(address => uint256) public balance;

    // constructor to initialize the token details
    constructor(string memory _name, string memory _abbrv) {
        tokenName = _name;
        tokenAbbrv = _abbrv;
    }

    // mint function
    function mint(address addr, uint256 _value) public {
        totalSupply += _value;
        balance[addr] += _value;                                  //increased balance
    }

    // burn function
    function burn(address addr, uint256 _value) public {
        require(balance[addr] >= _value, "Insufficient balance to burn");
        totalSupply -= _value;
        balance[addr] -= _value;                                                //decreased balance
    }
}
