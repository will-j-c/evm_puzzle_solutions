# evm_puzzle_solutions

## Puzzle 1

| Step | OpCode | Name      |
| ---- | ------ | --------- |
| 00   | 34     | CALLVALUE |
| 01   | 56     | JUMP      |
| 02   | FD     | REVERT    |
| 03   | FD     | REVERT    |
| 04   | FD     | REVERT    |
| 05   | FD     | REVERT    |
| 06   | FD     | REVERT    |
| 07   | FD     | REVERT    |
| 08   | 5B     | JUMPDEST  |
| 09   | 00     | STOP      |

**Solution**

Enter a value of 8. This puts 8 on the stack, then JUMP uses this to jump to 08.

## Puzzle 2

| Step | OpCode | Name      |
| ---- | ------ | --------- |
| 00   | 34     | CALLVALUE |
| 01   | 38     | CODESIZE  |
| 02   | 03     | SUB       |
| 03   | 56     | JUMP      |
| 04   | FD     | REVERT    |
| 05   | FD     | REVERT    |
| 06   | 5B     | JUMPDEST  |
| 07   | 00     | STOP      |
| 08   | FD     | REVERT    |
| 09   | FD     | REVERT    |

**Solution**

Enter a value of 4. This puts 4 on the stack, the CODESIZE is 10 as there are 10 instructions. SUB subtracts 4 from 10, leaving 6 on the stack. JUMP goes to instruction 6 (JUMPDEST) then STOP.

## Puzzle 3

| Step | OpCode | Name         |
| ---- | ------ | ------------ |
| 00   | 36     | CALLDATASIZE |
| 01   | 56     | JUMP         |
| 02   | FD     | REVERT       |
| 03   | FD     | REVERT       |
| 04   | 5B     | JUMPDEST     |
| 05   | 00     | STOP         |

**Solution**

Enter a value of 0x00000001. CALLDATASIZE returns the byte size of the call data. In hexidecimal, 2 character equal 1 byte. Therefore the above is 4 bytes, which in turn is ingested into JUMP to jump to instruction 4.

## Puzzle 4

| Step | OpCode | Name      |
| ---- | ------ | --------- |
| 00   | 34     | CALLVALUE |
| 01   | 38     | CODESIZE  |
| 02   | 18     | XOR       |
| 03   | 56     | JUMP      |
| 04   | FD     | REVERT    |
| 05   | FD     | REVERT    |
| 06   | FD     | REVERT    |
| 07   | FD     | REVERT    |
| 08   | FD     | REVERT    |
| 09   | FD     | REVERT    |
| 0A   | 5B     | JUMPDEST  |
| 0B   | 00     | STOP      |

**Solution**

Looking for a result of XOR to be 11. The binary representation of 10 is 1010.

The input of CODESIZE is 12, which is 1100 in binary. Therefore, the binary of the CALLVALUE must be 0110. Which is 6.

## Puzzle 5

| Step | OpCode | Name       |
| ---- | ------ | ---------- |
| 00   | 34     | CALLVALUE  |
| 01   | 80     | DUP1       |
| 02   | 02     | MUL        |
| 03   | 610100 | PUSH2 0100 |
| 06   | 14     | EQ         |
| 07   | 600C   | PUSH1 0C   |
| 09   | 57     | JUMP1      |
| 0A   | FD     | REVERT     |
| 0B   | FD     | REVERT     |
| 0C   | 5B     | JUMPDEST   |
| 0D   | 00     | STOP       |
| 0E   | FD     | REVERT     |
| 0F   | FD     | REVERT     |

**Solution**

In essence, the CALLVALUE must be equal to 10 in hexedecimal. It is duplicated, multiplied by itself and then matched against hexidecimal 100. If true, it jumps to the end point.

The answer is 16.

## Puzzle 6

| Step | OpCode | Name         |
| ---- | ------ | ------------ |
| 00   | 6000   | PUSH1 00     |
| 02   | 35     | CALLDATALOAD |
| 03   | 56     | JUMP         |
| 04   | FD     | REVERT       |
| 05   | FD     | REVERT       |
| 06   | FD     | REVERT       |
| 07   | FD     | REVERT       |
| 08   | FD     | REVERT       |
| 09   | FD     | REVERT       |
| 0A   | 5B     | JUMPDEST     |
| 0B   | 00     | STOP         |

**Solution**

CALLDATALOAD is calling the 32 bits starting form position 0. We need to jump to instruction 0A. bytes32 representation of 0A is 0x000000000000000000000000000000000000000000000000000000000000000a. This is the solution.

## Puzzle 7

| Step | OpCode | Name         |
| ---- | ------ | ------------ |
| 00   | 36     | CALLDATASIZE |
| 01   | 6000   | PUSH1 00     |
| 03   | 80     | DUP1         |
| 04   | 37     | CALLDATACOPY |
| 05   | 36     | CALLDATASIZE |
| 06   | 6000   | PUSH1 00     |
| 08   | 6000   | PUSH1 00     |
| 0A   | F0     | CREATE       |
| 0B   | 3B     | EXTCODESIZE  |
| 0C   | 6001   | PUSH1 01     |
| 0E   | 14     | EQ           |
| 0F   | 6013   | PUSH1 13     |
| 11   | 57     | JUMPI        |
| 12   | FD     | REVERT       |
| 13   | 5B     | JUMPDEST     |
| 14   | 00     | STOP         |

**Solution**

CALLDATALOAD is calling the 32 bits starting form position 0. We need to jump to instruction 0A. bytes32 representation of 0A is 0x000000000000000000000000000000000000000000000000000000000000000a. This is the solution.
