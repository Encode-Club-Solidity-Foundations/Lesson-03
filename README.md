# Lesson 3 - Syntax and structure
## Function definition
* Replacing memory with calldata when stack is enough
* Definitions
  * Visibility
  * State mutability
  * Modifiers
  * Virtual
  * Override
### References
https://docs.soliditylang.org/en/latest/introduction-to-smart-contracts.html#storage-memory-and-the-stack
### Code references
<pre><code>// SPDX-License-Identifier: GPL-3.0
pragma solidity >=0.7.0 <0.9.0;

contract HelloWorld {
    string private text;

    constructor() {
        text = "Hello World";
    }

    function helloWorld() public view returns (string memory)  {
        return text;
    }

    function setText(string calldata newText) public {
        text = newText;
    }
}</code></pre>
## Variable declaration and definition
* Elementary types
  * Booleans
  * Integers
  * Fixed
  * Address
  * Bytes
  * Strings
* State Variables
* Constants
* Data locations (again)
* Arrays
* Mappings
### References
https://docs.soliditylang.org/en/latest/types.html

## Exercises
* Extending new features

<pre><code>// SPDX-License-Identifier: GPL-3.0
pragma solidity >=0.7.0 <0.9.0;
contract HelloWorld {
    string private text;

    constructor() {
        text = pureText();
    }

    function helloWorld() public view returns (string memory) {
        return text;
    }

    function setText(string calldata newText) public {
        text = newText;
    }

    function pureText() public pure returns (string memory) {
        return "Hello World";
    }

    function _isPure() internal view returns (bool _check) {
        _check = keccak256(bytes(text)) == keccak256(bytes(pureText()));
    }

    function isPure() public view returns (bool _returnValue) {
        _returnValue = _isPure();
    }

    function _restore() internal {
        text = pureText();
    }

    function restore() public returns (bool) {
        if (_isPure()) return false;
        _restore();
        return true;
    }
}
</code></pre>

## Common Solidity Global Variables
* Reserved words and global variables that a programmer should know
* Global variables about blockchain state
* Global variables about the transaction
* Global variables about the transaction message
### References 
https://docs.soliditylang.org/en/latest/units-and-global-variables.html
## Assertion and Modifiers
* How errors are handled on solidity (briefly)
* Assertion
* Require statements
* Modifiers
* Where to use modifiers
### References
https://docs.soliditylang.org/en/latest/control-structures.html#error-handling-assert-require-revert-and-exceptions

https://docs.soliditylang.org/en/latest/structure-of-a-contract.html#function-modifiers
# Homework
* Create Github Issues with your questions about this lesson
* Read the references