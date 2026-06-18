# LOGIC Blocks

Logic blocks control the flow of execution: conditionals, loops, variables, tables, string manipulation, and function definitions.

---

## `ANDAny`
**Visual Name:** AND Gate
**Description:** AND Gate.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `A = {` | Any |
| `B = {` | Any |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Result = {` | Bool |

---

## `BreakLoop`
**Visual Name:** Break Loop
**Description:** Cancels the loop that this block is inside of.
**Context:** Server Only

**Inputs:** *(none)*

**Outputs:** *(none)*

---

## `CombineNumberWithString`
**Visual Name:** Combine Number With String
**Description:** Gives a string that is the inputted number followed by the inputted string. It is not possible to write new words this way, so the result will not be filtered. Because of that it is recommended to use this for countdowns.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Number = {` | Number |
| `AddSpace = {` | Bool |
| `String = {` | String |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Combined = {` | String |

---

## `CombineStringWithNumber`
**Visual Name:** Combine String With Number
**Description:** Gives a string that is the inputted number followed by the inputted string. It is not possible to write new words this way, so the result will not be filtered. Because of that it is recommended to use this for countdowns.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `String = {` | String |
| `AddSpace = {` | Bool |
| `Number = {` | Number |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Combined = {` | String |

---

## `Comparison`
**Visual Name:** Comparison
**Description:** Returns a boolean based on if the given condition is true.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Value 1 = {` | Any |
| `ComparisonType = {` | Choice |
| `Value 2 = {` | Any |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Result = {` | Bool |

---

## `Concatenate`
**Visual Name:** Combine Strings
**Description:** (Yields)(Filters) Combines 2 strings. The result will be filtered.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `FirstString = {` | String |
| `SecondString = {` | String |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Result = {` | String |

---

## `ContinueLoop`
**Visual Name:** Continue Loop
**Description:** Skips ahead to the next iteration of the loop that this block is apart of.
**Context:** Server Only

**Inputs:** *(none)*

**Outputs:** *(none)*

---

## `CreateTable`
**Visual Name:** Create Table
**Description:** Creates an empty table and stores it to the variable given.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:** *(none)*

**Outputs:**
| Name | Type Hint |
|---|---|
| `TableVariable = {` | Table |

---

## `DefineFunction`
**Visual Name:** Define Function
**Description:** Defines a function that can be called with the Execute Function block.
**Context:** All Scripts

**Inputs:** *(none)*

**Outputs:**
| Name | Type Hint |
|---|---|
| `TUPLE_Parameters = {` | — |

---

## `DoNotRun`
**Visual Name:** Do Not Run
**Description:** Does nothing and does not run its children blocks. Useful for temporarily disabling code, or to be used with ExecuteBlock.
**Context:** Server Only

**Inputs:** *(none)*

**Outputs:** *(none)*

---

## `ExecuteBlock`
**Visual Name:** Execute Block
**Description:** (Yields) Runs the block with the given name.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Name = {` | String |

**Outputs:** *(none)*

---

## `ExecuteFunction`
**Visual Name:** Execute Function
**Description:** (Yields) Executes a function. Connected blocks are ran after the function completes execution.
**Context:** All Scripts

**Inputs:**
| Name | Type |
|---|---|
| `Function = {` | Function |
| `Parameters = {` | Tuple |

**Outputs:**
| Name | Type Hint |
|---|---|
| `TUPLE_ReturnedValues = {` | — |

---

## `FilterString`
**Visual Name:** Filter String
**Description:** (Yields)(Filters) Filters a given string
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `String = {` | String |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Result = {` | String |

---

## `FindString`
**Visual Name:** Find String
**Description:** Looks for the first match of the given pattern.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `String = {` | String |
| `Pattern = {` | String |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Result = {` | Number |

---

## `ForLoop2`
**Visual Name:** For Loop
**Description:** Runs the connected blocks until Initial is equal to Maximum, while increasing Initial by Increment each time.
**Context:** All Scripts

**Inputs:**
| Name | Type |
|---|---|
| `Initial = {` | Number |
| `Increment = {` | Number |
| `Maximum = {` | Number |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Place = {` | Number |

---

## `FunctionReturn`
**Visual Name:** Function Return
**Description:** Ends execution of a function, and returns data to the execute function block.
**Context:** All Scripts

**Inputs:**
| Name | Type |
|---|---|
| `Returns = {` | Tuple |

**Outputs:** *(none)*

---

## `GSubString`
**Visual Name:** Global Sub String
**Description:** (Yields)(Filters) Returns a copy of the provided string in which all occurences of the pattern are replaced with the given replacement.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `String = {` | String |
| `Pattern = {` | String |
| `Replacement = {` | String |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Result = {` | String |

---

## `GetLength`
**Visual Name:** Get Length Of A String
**Description:** Returns the number of characters in an inputted string.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `String = {` | String |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Length = {` | Number |

---

## `GetTableLength`
**Visual Name:** Get Table Length
**Description:** Gives the length of a table. This will only work if all of the tables keys are integers.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Table = {` | Table |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Length = {` | Number |

---

## `GetTableValue`
**Visual Name:** Get Table Value
**Description:** Gets the value of a table at a specific key.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Table = {` | Table |
| `Key = {` | Any |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Value = {` | Any |

---

## `If`
**Visual Name:** If
**Description:** Runs connected blocks if the condition given is true, otherwise if given condition is false, runs the connected 'else' block using the right connector node.
**Context:** All Scripts

**Inputs:**
| Name | Type |
|---|---|
| `Value 1 = {` | Any |
| `ComparisonType = {` | Choice |
| `Value 2 = {` | Any |

**Outputs:** *(none)*

---

## `LoopThroughChildren`
**Visual Name:** Loop Through Children
**Description:** Runs the connected blocks once for each child of an object.
**Context:** All Scripts

**Inputs:**
| Name | Type |
|---|---|
| `Object = {` | Object |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Child = {` | Instance |

---

## `LoopThroughDescendants`
**Visual Name:** Loop Through Descendants
**Description:** Runs the connected blocks once for each descendant of an object.
**Context:** All Scripts

**Inputs:**
| Name | Type |
|---|---|
| `Object = {` | Object |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Descendant = {` | Instance |

---

## `LoopThroughTable`
**Visual Name:** Loop Through Table
**Description:** Runs the connected blocks once for each value in a table.
**Context:** All Scripts

**Inputs:**
| Name | Type |
|---|---|
| `Table = {` | Table |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Index = {` | Any |

---

## `Lower`
**Visual Name:** Lower
**Description:** Turns all characters in the string to lower-case
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `String = {` | String |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Result = {` | String |

---

## `NOTAny`
**Visual Name:** NOT Gate
**Description:** Inverter Gate.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `A = {` | Any |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Result = {` | Bool |

---

## `ORAny`
**Visual Name:** OR Gate
**Description:** OR Gate.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `A = {` | Any |
| `B = {` | Any |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Result = {` | Bool |

---

## `Require`
**Visual Name:** Require
**Description:** (Yields) Executes a ModuleScript and recieves data from its Module Return block. Useful for sharing code or data between multiple scripts.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `ModuleScript = {` | Object |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Returned = {` | Any |

---

## `SetTableValue`
**Visual Name:** Set Table Value
**Description:** Sets the value of a table at a specific key.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Table = {` | Table |
| `Key = {` | Any |
| `Value = {` | Any |

**Outputs:** *(none)*

---

## `SetVariable1`
**Visual Name:** Set Variable
**Description:** Sets a variable.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Value = {` | Any |

**Outputs:**
| Name | Type Hint |
|---|---|
| `VariableName = {` | Any |

---

## `SortTable`
**Visual Name:** Sort Table
**Description:** Sorts a table based on each value. The table should be formatted like an array.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Table = {` | Table |
| `Order = {` | Choice |

**Outputs:** *(none)*

---

## `SortTableAdvanced`
**Visual Name:** Sort Table Advanced
**Description:** Sorts a table based on its values. For each value in the table, the blocks connected to this one will run. There should be a Sort Table Advanced Return block connected to this one that returns True if ValueA should be before ValueB. An "Invalid order given for sorting." error will be thrown if ValueA is set to be both before and after ValueB. The table should be formatted like an array.
**Context:** All Scripts

**Inputs:**
| Name | Type |
|---|---|
| `Table = {` | Table |

**Outputs:**
| Name | Type Hint |
|---|---|
| `ValueA = {` | Any |

---

## `SortTableAdvancedReturn`
**Visual Name:** Sort Table Advanced Return
**Description:** Returns True or False to the Sort Table Advanced block to determine the order of values in the table.
**Context:** All Scripts

**Inputs:**
| Name | Type |
|---|---|
| `Return = {` | Bool |

**Outputs:** *(none)*

---

## `Spawn`
**Visual Name:** Spawn
**Description:** Executes a function. Connected and adjacent blocks are ran immediately, rather than waiting for the function to finish.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Function = {` | Function |
| `Parameters = {` | Tuple |

**Outputs:** *(none)*

---

## `SplitString`
**Visual Name:** Split String
**Description:** Splits a string into parts based on the defined seperator character(s), returning a table of ordered results.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `String = {` | String |
| `Seperator = {` | String |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Result = {` | String |

---

## `Substring`
**Visual Name:** Substring
**Description:** (Filters) Returns the substring of an inputted string that starts at the first number to the last number.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `String = {` | String |
| `StartPoint = {` | Number |
| `EndPoint = {` | Number |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Result = {` | String |

---

## `TableAppend`
**Visual Name:** Table Append
**Description:** Places a value at the end of a table. This will only work if all of the tables keys are integers.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Table = {` | Table |
| `Value = {` | Any |

**Outputs:** *(none)*

---

## `TableFind`
**Visual Name:** Find in Table
**Description:** Finds the first occurance of a value in a table and outputs the key. If the value is not found within the table, nil is outputted. An optional init value can be supplied, which will cause the search to start at that key.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Table = {` | Table |
| `Value = {` | Any |
| `Init = {` | Number |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Key = {` | Any |

---

## `TableInsert`
**Visual Name:** Table Insert
**Description:** Places a value into a table at the specified position. This will only work if all of the tables keys are integers.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Table = {` | Table |
| `Position = {` | Number |
| `Value = {` | Any |

**Outputs:** *(none)*

---

## `TablePack`
**Visual Name:** Pack Table
**Description:** Pack a tuple of values into a table array.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Values = {` | Tuple |

**Outputs:**
| Name | Type Hint |
|---|---|
| `TableVariable = {` | Table |

---

## `TableRemove`
**Visual Name:** Table Remove
**Description:** Removes a value from a table at the specified position. This will only work if all of the tables keys are integers.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Table = {` | Table |
| `Position = {` | Number |

**Outputs:** *(none)*

---

## `TableUnpack`
**Visual Name:** Unpack Table
**Description:** Unpack table array and return a tuple of its values
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Table = {` | Table |

**Outputs:**
| Name | Type Hint |
|---|---|
| `TUPLE_Values = {` | — |

---

## `ToNumberAny`
**Visual Name:** To Number
**Description:** Tries to convert a value to a number. If this is not possible, nil is given.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Input = {` | Any |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Number = {` | Number |

---

## `ToStringAny`
**Visual Name:** To String
**Description:** Converts a value to a string.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Input = {` | Any |

**Outputs:**
| Name | Type Hint |
|---|---|
| `String = {` | String |

---

## `TypeOf`
**Visual Name:** Type Of
**Description:** Returns the type of a variable.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:** *(none)*

**Outputs:**
| Name | Type Hint |
|---|---|
| `Type = {` | String |

---

## `Upper`
**Visual Name:** Upper
**Description:** Turns all characters in the string to capitals
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `String = {` | String |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Result = {` | String |

---

## `Wait`
**Visual Name:** Wait
**Description:** Waits a certain amount of time and then runs the connected blocks.
**Context:** All Scripts

**Inputs:**
| Name | Type |
|---|---|
| `Time = {` | Number |

**Outputs:** *(none)*

---

## `WhileLoop3`
**Visual Name:** While Loop
**Description:** Repeatedly runs the connected blocks until the given condition is false.
**Context:** All Scripts

**Inputs:**
| Name | Type |
|---|---|
| `Value 1 = {` | Any |
| `ComparisonType = {` | Choice |
| `Value 2 = {` | Any |

**Outputs:** *(none)*

---
