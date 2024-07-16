pragma solidity 0.8.17;

// SPDX-License-Identifier: MIT

contract HMSTR {
  string public name = "Hamster Network";
  string public symbol = "HMSTR";
  uint8 public decimals = 18;
  uint256 public totalSupply = 10000000000 * 10 ** uint256(decimals);

  mapping (address => uint256) public balances;
  mapping (address => mapping (address => uint256)) public allowance;

  address public owner;

  event Transfer(address indexed from, address indexed to, uint256 value);
  event Approval(address indexed owner, address indexed spender, uint256 value);

  constructor() {
    owner = msg.sender;
    balances[owner] = totalSupply;
    emit Transfer(address(0), owner, totalSupply);
  }

  function balanceOf(address account) public view returns (uint256) {
    return balances[account];
  }

  function transfer(address recipient, uint256 amount) public returns (bool) {
    require(balances[msg.sender] >= amount, "Insufficient balance.");
    balances[msg.sender] -= amount;
    balances[recipient] += amount;
    emit Transfer(msg.sender, recipient, amount);
    return true;
  }

  function approve(address spender, uint256 amount) public returns (bool) {
    allowance[msg.sender][spender] = amount;
    emit Approval(msg.sender, spender, amount);
    return true;
  }

  function transferFrom(address sender, address recipient, uint256 amount) public returns (bool) {
    require(balances[sender] >= amount, "Insufficient balance.");
    require(allowance[sender][msg.sender] >= amount, "Allowance exceeded.");
    balances[sender] -= amount;
    balances[recipient] += amount;
    allowance[sender][msg.sender] -= amount;
    emit Transfer(sender, recipient, amount);
    return true;
  }
}