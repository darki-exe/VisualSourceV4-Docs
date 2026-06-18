# MATH Blocks

Math blocks perform arithmetic, vector operations, CFrame transformations, color conversions, and random number generation.

---

## `Addition`
**Visual Name:** Addition
**Description:** Perform addition on two numbers, Vector3s or CFrames.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Number1 = {` | Number |
| `Number2 = {` | Number |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Result = {` | Number |

---

## `Angles`
**Visual Name:** CFrame Angles
**Description:** Returns a rotated CFrame using angles x, y, & z.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `rx = {` | Number |
| `ry = {` | Number |
| `rz = {` | Number |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Result = {` | CFrame |

---

## `BrickColorToColor3`
**Visual Name:** BrickColor To Color3
**Description:** Converts a BrickColor to a Color3
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `BrickColor = {` | BrickColor |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Color3 = {` | Color3 |

---

## `Color3ToBrickColor`
**Visual Name:** Color3 to BrickColor
**Description:** Converts a Color3 to the closest existing BrickColor
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Color3 = {` | Color3 |

**Outputs:**
| Name | Type Hint |
|---|---|
| `BrickColor = {` | BrickColor |

---

## `Color3ToHSV`
**Visual Name:** Color3 to HSV
**Description:** Converts a Color3 to HSV values
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Color3 = {` | Color3 |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Hue = {` | Number |

---

## `ConstructCFrame`
**Visual Name:** Construct CFrame
**Description:** Constructs a CFrame value from a position and rotation.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Position = {` | Vector3 |
| `Rotation = {` | Vector3 |

**Outputs:**
| Name | Type Hint |
|---|---|
| `CFrame = {` | CFrame |

---

## `ConstructColor3`
**Visual Name:** Construct Color3
**Description:** Creates a Color3 value from the given numbers. Inputted numbers must range between 0 and 255.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `R = {` | Number |
| `G = {` | Number |
| `B = {` | Number |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Color3 = {` | Color3 |

---

## `ConstructNumberRange`
**Visual Name:** Construct NumberRange
**Description:** Creates a NumberRange variable from the 2 given numbers.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Min = {` | Number |
| `Max = {` | Number |

**Outputs:**
| Name | Type Hint |
|---|---|
| `NumberRange = {` | NumberRange |

---

## `ConstructUDim2`
**Visual Name:** Construct UDim2
**Description:** Creates a UDim2 value from the given numbers.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `XScale = {` | Number |
| `XOffset = {` | Number |
| `YScale = {` | Number |
| `YOffset = {` | Number |

**Outputs:**
| Name | Type Hint |
|---|---|
| `UDim2 = {` | UDim2 |

---

## `ConstructVector2`
**Visual Name:** Construct Vector2
**Description:** Creates a Vector2 variable from the 2 given numbers.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `X = {` | Number |
| `Y = {` | Number |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Vector2 = {` | Vector2 |

---

## `ConstructVector3`
**Visual Name:** Construct Vector3
**Description:** Creates a Vector3 variable from the 3 given numbers.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `X = {` | Number |
| `Y = {` | Number |
| `Z = {` | Number |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Vector3 = {` | Vector3 |

---

## `DistanceBetweenPoints`
**Visual Name:** Distance Between Points
**Description:** Gives the distance between 2 Vector3 values.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Point 1 = {` | Vector3 |
| `Point 2 = {` | Vector3 |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Distance = {` | Number |

---

## `Division`
**Visual Name:** Division
**Description:** Perform division on two numbers or vector3s.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Number1 = {` | Number |
| `Number2 = {` | Number |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Result = {` | Number |

---

## `Exponentiation`
**Visual Name:** Exponentiation
**Description:** Perform exponentiation on two numbers. For lua users, this is the same as the ^ operator
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Number1 = {` | Number |
| `Number2 = {` | Number |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Result = {` | Number |

---

## `FromAxisAngle`
**Visual Name:** From Axis Angle
**Description:** Returns a rotated CFrame from a unit Vector3 and a rotation in radians.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `v = {` | Vector3 |
| `r = {` | number |

**Outputs:**
| Name | Type Hint |
|---|---|
| `CFrame = {` | CFrame |

---

## `FromMatrix`
**Visual Name:** From Matrix
**Description:** Returns a CFrame from a translation and the columns of a rotation matrix. If vZ is excluded, the third column is calculated as vX:Cross(vY).Unit
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `pos = {` | Vector3 |
| `vX = {` | Vector3 |
| `vY = {` | Vector3 |
| `vZ = {` | Vector3 |

**Outputs:**
| Name | Type Hint |
|---|---|
| `CFrame = {` | CFrame |

---

## `GetCFrameDirection`
**Visual Name:** Get CFrame Direction
**Description:** Gives the direction a cframe is facing
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `CFrame = {` | CFrame |
| `Direction = {` | Choice |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Direction = {` | Vector3 |

---

## `GetPartDirection`
**Visual Name:** Get Part Direction
**Description:** Gives the direction a part is facing
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Part = {` | Object |
| `Direction = {` | Choice |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Direction = {` | Vector3 |

---

## `HSVToColor3`
**Visual Name:** HSV To Color3
**Description:** Converts HSV values to Color3
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Hue = {` | Number |
| `Saturation = {` | Number |
| `Value = {` | Number |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Color3 = {` | Color3 |

---

## `InverseCFrame1`
**Visual Name:** Inverse CFrame
**Description:** Returns the inverse of a cframe.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `CFrame = {` | CFrame |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Result = {` | CFrame |

---

## `Lerp1`
**Visual Name:** Lerp
**Description:** Returns a cframe interpolated between itself and a goal by the given alpha.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `StartCFrame = {` | CFrame |
| `GoalCFrame = {` | CFrame |
| `Alpha = {` | Number |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Result = {` | CFrame |

---

## `MathLibraryDoubleInput`
**Visual Name:** Math Library Double Input
**Description:** Functions in the lua math library with two inputs.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Function = {` | Choice |
| `Number1 = {` | Number |
| `Number2 = {` | Number |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Result = {` | Number |

---

## `MathLibrarySingleInput`
**Visual Name:** Math Library Single Input
**Description:** Functions in the lua math library with only one input.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Function = {` | Choice |
| `Number = {` | Number |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Result = {` | Number |

---

## `MathLibraryTripleInput`
**Visual Name:** Math Library Triple Input
**Description:** Functions in the lua math library with three inputs.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Function = {` | Choice |
| `Number1 = {` | Number |
| `Number2 = {` | Number |
| `Number3 = {` | Number |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Result = {` | Number |

---

## `Modulus`
**Visual Name:** Modulus
**Description:** Perform modulus on two numbers.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Number1 = {` | Number |
| `Number2 = {` | Number |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Result = {` | Number |

---

## `Multiplication`
**Visual Name:** Multiplication
**Description:** Perform multiplication on two numbers, Vector3s or CFrames.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Number1 = {` | Number |
| `Number2 = {` | Number |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Result = {` | Number |

---

## `NormalizeVector3`
**Visual Name:** Normalize Vector3
**Description:** Takes a Vector3 value and gives a modified version of it that has the same direction but a total distance of 1.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Vector3 = {` | Vector3 |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Result = {` | Vector3 |

---

## `PerlinNoise`
**Visual Name:** Perlin Noise
**Description:** Outputs a perlin noise value. The result is generally between -1 and 1, but may be outside of that range. If all 3 inputs are integers, the result will always be 0.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `X = {` | Number |
| `Y = {` | Number |
| `Z = {` | Number |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Result = {` | Number |

---

## `RandomBrickColor`
**Visual Name:** Random BrickColor
**Description:** Outputs a random BrickColor.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:** *(none)*

**Outputs:**
| Name | Type Hint |
|---|---|
| `BrickColor = {` | BrickColor |

---

## `RandomNumber`
**Visual Name:** Random Number
**Description:** Returns a random number between two given numbers.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Minimum = {` | Number |
| `Maximum = {` | Number |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Result = {` | Numbner |

---

## `RotationBetweenPoints`
**Visual Name:** Rotation Between Points
**Description:** Gives the orientation needed to make a part at Point 1 face towards Point 2
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Point 1 = {` | Vector3 |
| `Point 2 = {` | Vector3 |

**Outputs:**
| Name | Type Hint |
|---|---|
| `RotationVector3 = {` | Vector3 |

---

## `Round`
**Visual Name:** Round
**Description:** Rounds a number.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Number = {` | Number |
| `Type = {` | Choice |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Result = {` | Number |

---

## `SolveEquation`
**Visual Name:** Solve Equation
**Description:** Solves a math equation. For example, the equation "2 + 2" would output 4. Uses similar syntax to Lua, and is intended for users familiar with the language. Not all lua features are supported, the following is a list of what is: - This supports the +, -, *, /, %, and ^ operators. - This can read variables (Must not start with a number or include special characters in the name!) - This can call user made functions. - This can use the Lua math library. - This supports constructing and calling functions on the following data types: Vector3, Vector2, UDim2, UDim, CFrame, Color3, ColorSequence, NumberSequence
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Equation = {` | Equation |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Result = {` | Any |

---

## `SplitCFrame`
**Visual Name:** Split CFrame
**Description:** Splits a CFrame value into its position and rotation.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `CFrame = {` | CFrame |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Position = {` | Vector3 |

---

## `SplitColor3`
**Visual Name:** Split Color3
**Description:** Splits a Color3 value into its components.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Color3 = {` | Color3 |

**Outputs:**
| Name | Type Hint |
|---|---|
| `R = {` | Number |

---

## `SplitNumberRange`
**Visual Name:** Split NumberRange
**Description:** Splits a NumberRange value into its components.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `NumberRange = {` | NumberRange |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Min = {` | Number |

---

## `SplitUDim2`
**Visual Name:** Split UDim2
**Description:** Splits a UDim2 value into its components.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `UDim2 = {` | UDim2 |

**Outputs:**
| Name | Type Hint |
|---|---|
| `XScale = {` | Number |

---

## `SplitVector2`
**Visual Name:** Split Vector2
**Description:** Splits a Vector2 value into its components.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Vector2 = {` | Vector2 |

**Outputs:**
| Name | Type Hint |
|---|---|
| `X = {` | Number |

---

## `SplitVector3`
**Visual Name:** Split Vector3
**Description:** Splits a Vector3 value into its components.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Vector3 = {` | Vector3 |

**Outputs:**
| Name | Type Hint |
|---|---|
| `X = {` | Number |

---

## `Subtraction`
**Visual Name:** Subtraction
**Description:** Perform subtraction on two numbers, Vector3s or CFrames.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Number1 = {` | Number |
| `Number2 = {` | Number |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Result = {` | Number |

---

## `ToEulerAnglesXYZ`
**Visual Name:** To Euler Angles XYZ
**Description:** Returns approximate angles that could be used to generate the CFrame.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `CFrame = {` | CFrame |

**Outputs:**
| Name | Type Hint |
|---|---|
| `rx = {` | Number |

---

## `ToObjectSpace1`
**Visual Name:** To Object Space
**Description:** Transforms a cframe to object space.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `CFrame = {` | CFrame |
| `ObjectCFrame = {` | CFrame |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Result = {` | CFrame |

---

## `ToWorldSpace1`
**Visual Name:** To World Space
**Description:** Transforms a cframe to world space.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `CFrame = {` | CFrame |
| `ObjectCFrame = {` | CFrame |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Result = {` | CFrame |

---

## `Vector3Cross`
**Visual Name:** Vector3 Cross
**Description:** Gives the cross product of two vectors
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `VectorA = {` | Vector3 |
| `VectorB = {` | Vector3 |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Result = {` | Vector3 |

---

## `Vector3Dot`
**Visual Name:** Vector3 Dot
**Description:** Gives the dot product of two vectors
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `VectorA = {` | Vector3 |
| `VectorB = {` | Vector3 |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Result = {` | Number |

---
