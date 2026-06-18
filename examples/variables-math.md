# Variables & Math

Examples for storing values, doing arithmetic, working with strings, and using random numbers.

---

## Set a Variable

Store a number (15) into a variable named `my_variable`.

```
Editor CameraPosition 0,0 CameraZoom 0.1C2  Block Type SetVariable1 Name Set Variable1 VisualPosition -0.36B,0 ChildBlocks ElseChildBlock nil Inputs Value 0 F Outputs VariableName my_variable
```

> `F` in hex = 15

---

## Addition

Add two numbers and store the result.

```
Editor CameraPosition -0.81,0.1C6 CameraZoom 0.1C2  Block Type Addition Name Addition1 VisualPosition -0.36B,0.7D ChildBlocks Set Variable2 ElseChildBlock nil Inputs Number1 2 my_variable Number2 0 6 Outputs Result result  Block Type SetVariable1 Name Set Variable1 VisualPosition -0.36B,-0.1F4 ChildBlocks Addition1 ElseChildBlock nil Inputs Value 1 F Number Outputs VariableName my_variable  Block Type SetVariable1 Name Set Variable2 VisualPosition -0.36B,0.2EE ChildBlocks ElseChildBlock nil Inputs Value 2 result Outputs VariableName my_variable
```

**What it does:**
1. `Set Variable1` sets `my_variable` to 15 (`F` hex)
2. `Addition1` adds `my_variable` + 6, outputs to `result`
3. `Set Variable2` stores `result` back into `my_variable`

---

## Subtraction

```
Editor CameraPosition -0.3A,0.282 CameraZoom 0.1C2  Block Type Subtraction Name Subtraction1 VisualPosition -0.36B,0.7D ChildBlocks Set Variable2 ElseChildBlock nil Inputs Number1 2 my_variable Number2 0 6 Outputs Result result  Block Type SetVariable1 Name Set Variable1 VisualPosition -0.36B,-0.1F4 ChildBlocks Subtraction1 ElseChildBlock nil Inputs Value 1 F Number Outputs VariableName my_variable  Block Type SetVariable1 Name Set Variable2 VisualPosition -0.36B,0.2EE ChildBlocks ElseChildBlock nil Inputs Value 2 result Outputs VariableName my_variable
```

---

## Multiplication

```
Editor CameraPosition -0.81,0.1C6 CameraZoom 0.1C2  Block Type Multiplication Name Multiplication1 VisualPosition -0.36B,0.7D ChildBlocks Set Variable2 ElseChildBlock nil Inputs Number1 2 my_variable Number2 0 6 Outputs Result result  Block Type SetVariable1 Name Set Variable1 VisualPosition -0.36B,-0.1F4 ChildBlocks Multiplication1 ElseChildBlock nil Inputs Value 1 F Number Outputs VariableName my_variable  Block Type SetVariable1 Name Set Variable2 VisualPosition -0.36B,0.2EE ChildBlocks ElseChildBlock nil Inputs Value 2 result Outputs VariableName my_variable
```

---

## Division

```
Editor CameraPosition -0.81,0.1C6 CameraZoom 0.1C2  Block Type Division Name Division1 VisualPosition -0.36B,0.7D ChildBlocks Set Variable2 ElseChildBlock nil Inputs Number1 2 my_variable Number2 0 6 Outputs Result result  Block Type SetVariable1 Name Set Variable1 VisualPosition -0.36B,-0.1F4 ChildBlocks Division1 ElseChildBlock nil Inputs Value 1 F Number Outputs VariableName my_variable  Block Type SetVariable1 Name Set Variable2 VisualPosition -0.36B,0.2EE ChildBlocks ElseChildBlock nil Inputs Value 2 result Outputs VariableName my_variable
```

---

## Modulus

Returns the remainder of a division.

```
Editor CameraPosition -0.95,0.191 CameraZoom 0.1C2  Block Type Modulus Name Modulus1 VisualPosition -0.36B,0.7D ChildBlocks Set Variable2 ElseChildBlock nil Inputs Number1 2 my_variable Number2 0 6 Outputs Result result  Block Type SetVariable1 Name Set Variable2 VisualPosition -0.36B,0.2EE ChildBlocks ElseChildBlock nil Inputs Value 2 result Outputs VariableName my_variable  Block Type SetVariable1 Name Set Variable1 VisualPosition -0.36B,-0.1F4 ChildBlocks Modulus1 ElseChildBlock nil Inputs Value 1 F Number Outputs VariableName my_variable
```

---

## Random Number

Generate a random number between 0 and 10, store it in a variable.

```
Editor CameraPosition -0.A2,-0.369 CameraZoom 0.1C2  Block Type SetVariable1 Name Set Variable1 VisualPosition -0.36B,-0.1F4 ChildBlocks ElseChildBlock nil Inputs Value 2 rng Outputs VariableName my_variable  Block Type RandomNumber Name Random Number1 VisualPosition -0.36B,-1.7D ChildBlocks Set Variable1 ElseChildBlock nil Inputs Minimum 0 0 Maximum 0 A Outputs Result rng
```

> `A` hex = 10

---

## Solve Equation

Use a formula string to compute complex expressions.

```
Editor CameraPosition -0.23A,0.FC CameraZoom 0.1C2  Block Type SetVariable1 Name Set Variable2 VisualPosition -0.36B,0.2EE ChildBlocks ElseChildBlock nil Inputs Value 2 result Outputs VariableName my_variable  Block Type SolveEquation Name Solve Equation1 VisualPosition -0.36B,0.7D ChildBlocks Set Variable2 ElseChildBlock nil Inputs Equation 0 my_variable + 6 + (6 - 5) / 2 + (12 * 6 / 3) Outputs Result result  Block Type SetVariable1 Name Set Variable1 VisualPosition -0.36B,-0.1F4 ChildBlocks Solve Equation1 ElseChildBlock nil Inputs Value 1 F Number Outputs VariableName my_variable
```

The `Equation` input accepts a math expression as a string, with variable names referenced by name.

---

## Concatenate Strings

Combine a player name and a message.

```
Editor CameraPosition 0,0 CameraZoom 0.1C2  Block Type Concatenate Name Concatenate1 VisualPosition -0.36B,0 ChildBlocks Print1 ElseChildBlock nil Inputs String1 1 player_name String2 0  joined the game Outputs Result message  Block Type Print Name Print1 VisualPosition -0.36B,0.271 ChildBlocks ElseChildBlock nil Inputs Text 1 message Outputs
```
