
Certain MathWorks Simulink® functionality is disabled while building
VeriStand models.

## Solver Constraints

The solver only supports the **Fixed-step** type. The Fixed-step size
(fundamental sample time) parameter value has limitations. Automatic
step size is not supported. Expressions containing variables with
`Simulink.Parameter` or `Simulink.Signal` type are not supported unless
the expression represents a simple variable name. For example, `var` is
supported, but `var + 1` is not if *var* is one of the two types. This
constraint applies only to `Simulink.Parameter` or `Simulink.Signal`
operands. VeriStand supports expressions containing variables with
base-supported data types. A step size from the model may differ from
the actual step size. VeriStand always uses a six-digit precision number
for the step size.\
\
For periodic sample time constraint, only **Unconstrained** and **Ensure
sample time independent** are supported. The **Automatically handle rate
transition for data transfer** is checked but not enforced. This option
does not exist if the sample time constraint is **Ensure sample time
independent**. Also, this option won\'t be checked by default if the
sample time constraint is set to **Ensure sample time independent** when
selecting the veristand.tlc and setting the **Unconstrained** value
later.\
\
The **Treat each discrete rate as a separate task** option is enabled
and enforced.

## Unsupported Data Types

VeriStand models support nonvirtual bus, numeric, and Boolean Simulink
data types. The following data types are not supported:

-   Strings
-   Enums
-   Array of buses
-   Arrays with more than 2 dimensions
-   Fixed-Point numeric data types
-   Complex numeric data types

**Note**: Models with these data types can be built if the **Turn
warnings into errors for unsupported data types** option is disabled.\
\
Virtual bus outports are not supported. Depending on the configuration,
either an error or warning is generated while building the model. Bus
element ports are not supported, regardless of configuration.\
\
When treated as warnings, the ports, parameters or bus elements that
have unsupported data types are ignored by VeriStand when importing and
running the model. You are not able to get or set values for those
ports, parameters or bus elements.

## Arrays Layout

Arrays are stored using a column-major order. VeriStand supports the
same layout for arrays, making this order the highest-performance choice

## Code Interface

The **Nonreusable function** option is enforced.\
\
The **Single output/update function** option is disabled and greyed out.

## Signals

Enabling bus type signals is not supported.

## Hardware Implementation

The **Support long long** option must be enabled. If disabled, an error
will occur at build time.

## Nonvirtual Bus Types Naming

Nonvirtual bus types that have the same name as Simulink multiword
struct definitions are not supported and an error is generated while
building the model. These names match the following patterns:

-   int*\<num\>*m_T
-   cint*\<num\>*m_T
-   uint*\<num\>*m_T
-   cuint*\<num\>*m_T

**Note**: The *\<num\>* variable represents a multiple of 64 and that is
greater or equal than 128. This is true regardless of the value of
Maximum word length (`MultiwordLength`).