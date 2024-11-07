### 9.1
#### We started of by doing it for the main function by mistake so here is that one
```
IL_0000: nop                                                                            // Do nothing
IL_0001: ldc.i4.s 10                                                                    // Push 10 to stack
IL_0003: stloc.0                                                                        // Store variable on 0
IL_0004: ldloc.0                                                                        // Load local variable 0
IL_0005: newarr [System.Runtime]System.Int32                                            // Make array
IL_000a: stloc.1                                                                        // Store array on 1
IL_000b: ldc.i4.0                                                                       // Push 0 onto the stack
IL_000c: stloc.2                                                                        // Store local variable 2
IL_000d: br.s IL_0025                                                                   // Unconditional jump to IL_0025
// loop start (head: IL_0025)
    IL_000f: ldloc.1                                                                    // Load local variable 1
    IL_0010: ldloc.2                                                                    // Load local variable 2
    IL_0011: ldsfld class [System.Runtime]System.Random Selsort::rnd                    // Push random number
    IL_0016: ldc.i4 1000000                                                             // Push 1000000
    IL_001b: callvirt instance int32 [System.Runtime]System.Random::Next(int32)         // Method call associated with object
    IL_0020: stelem.i4                                                                  // Replace array element with the variable
    IL_0021: ldloc.2                                                                    // Load local variable 2
    IL_0022: ldc.i4.1                                                                   // Push 1 onto the stack
    IL_0023: add                                                                        // Add 1 to variable 2 
    IL_0024: stloc.2                                                                    // Store new variable in 2

    IL_0025: ldloc.2                                                                    // Load local variable 2
    IL_0026: ldloc.0                                                                    // Load local variable 0
    IL_0027: clt                                                                        // Compare the two variables. Push 1 if ->
                                                                                        // variable 2 < variable 0
    IL_0029: stloc.3                                                                    // Store result in local variable 3
    IL_002a: ldloc.3                                                                    // Load local variable 3
    IL_002b: brtrue.s IL_000f                                                           // Jump to IL_000f if local variable 3 != 0
// end loop

IL_002d: ldloc.1                                                                        // Load local variable 1
IL_002e: call void Selsort::SelectionSort(int32[])                                      // Call SelectionSort
IL_0033: nop                                                                            // Do nothing
IL_0034: ldc.i4.0                                                                       // Push 0 onto the stack
IL_0035: stloc.s 4                                                                      // Store in local variable 4
IL_0037: br.s IL_005c                                                                   // Unconditional jump to IL_005c
// loop start (head: IL_005c)
    IL_0039: ldloc.1                                                                    // Load local variable 1
    IL_003a: ldloc.s 4                                                                  // Load local variable 4
    IL_003c: ldelema [System.Runtime]System.Int32                                       // Load address of System.Int32
    IL_0041: call instance string [System.Runtime]System.Int32::ToString()              // Call ToString
    IL_0046: ldstr " "                                                                  // Push " "
    IL_004b: call string [System.Runtime]System.String::Concat(string, string)          // Concat " " with Int32 that has been made 
                                                                                        // To a string
    IL_0050: call void [System.Console]System.Console::Write(string)                    // Call Write
    IL_0055: nop                                                                        // Do nothing
    IL_0056: ldloc.s 4                                                                  // Load local variable 4
    IL_0058: ldc.i4.1                                                                   // Push 1 onto the stack
    IL_0059: add                                                                        // Add 1 to local variable 4
    IL_005a: stloc.s 4                                                                  // Store result in local variable 4

    IL_005c: ldloc.s 4                                                                  // Load local variable 4
    IL_005e: ldloc.0                                                                    // Load local variable 0
    IL_005f: clt                                                                        // Compare the two variables. Push 1 if ->
                                                                                        // variable 4 < variable 0 
    IL_0061: stloc.s 5                                                                  // Store result in local variable 5
    IL_0063: ldloc.s 5                                                                  // Load local variable 5
    IL_0065: brtrue.s IL_0039                                                           // Jump to IL_0039 if local variable 5 != 0
// end loop

IL_0067: call void [System.Console]System.Console::WriteLine()                          // Call WriteLine
IL_006c: nop                                                                            // Do nothing
IL_006d: ret                                                                            // Return
```


#### (i - C#)

Here is the correct one:
Local variable 0 = i
Local variable 1 = least
Local variable 2 = tmp
Local variable 3 = j

```
IL_0000: nop                                                                            // Do nothing
IL_0001: ldc.i4.0                                                                       // Push 0 onto the stack
IL_0002: stloc.0                                                                        // Store local variable 0
IL_0003: br.s IL_0041                                                                   // Unconditional jump to IL_0041
// loop start (head: IL_0041)
    IL_0005: nop                                                                        // Do nothing
    IL_0006: ldloc.0                                                                    // Load local variable 0
    IL_0007: stloc.1                                                                    // Store local variable 1
    IL_0008: ldloc.0                                                                    // Load local variable 0
    IL_0009: ldc.i4.1                                                                   // Push 1 to the stack
    IL_000a: add                                                                        // Add 1 to local variable 0
    IL_000b: stloc.3                                                                    // Store the result in local variable 3
    IL_000c: br.s IL_0022                                                               // Unconditional jump to IL_0022
    // loop start (head: IL_0022)
        IL_000e: ldarg.0                                                                // Load the array (arg 0) onto the stack
        IL_000f: ldloc.3                                                                // Load the local variable 3
        IL_0010: ldelem.i4                                                              // Load the element on the ->
                                                                                        // arr[local variable 3]
        IL_0011: ldarg.0                                                                // Load the array (arg 0) onto the stack
        IL_0012: ldloc.1                                                                // Load the local variable 1
        IL_0013: ldelem.i4                                                              // Load the element on the ->
                                                                                        // arr[local variable 1]
        IL_0014: clt                                                                    // Compare the two arr[i] values. Push 1 ->
                                                                                        // If arr[var 3] < arr[var 1]
        IL_0016: stloc.s 4                                                              // Store the result in local variable 4
        IL_0018: ldloc.s 4                                                              // Load local variable 4
        IL_001a: brfalse.s IL_001e                                                      // Jump to IL_001e if local variable 4 == 0

        IL_001c: ldloc.3                                                                // Load local variable 3 (j)
        IL_001d: stloc.1                                                                // Store in local variable 1 (least)

        IL_001e: ldloc.3                                                                // Load local variable 3
        IL_001f: ldc.i4.1                                                               // Push 1 onto the stack
        IL_0020: add                                                                    // Add local variable with 1
        IL_0021: stloc.3                                                                // Store the result in local variable 3

        IL_0022: ldloc.3                                                                // Load local variable 3
        IL_0023: ldarg.0                                                                // Load the array (arg 0) onto the stack
        IL_0024: ldlen                                                                  // Push the length of the array to the stack
        IL_0025: conv.i4                                                                // Convert to int32
        IL_0026: clt                                                                    // Compare the two variables. Push 1 if ->
                                                                                        // variable 3 < length of the array
        IL_0028: stloc.s 5                                                              // Store the result in local variable 5
        IL_002a: ldloc.s 5                                                              // Load local variable 5
        IL_002c: brtrue.s IL_000e                                                       // Jump to IL_000e if local variable 5 != 0
    // end loop

    IL_002e: ldarg.0                                                                    // Load the array (arg 0) onto the stack
    IL_002f: ldloc.0                                                                    // Load local variable 0
    IL_0030: ldelem.i4                                                                  // Load the element on the ->
                                                                                        // arr[local variable 0]
    IL_0031: stloc.2                                                                    // Store the result in local variable 2
    IL_0032: ldarg.0                                                                    // Load the array (arg 0) onto the stack
    IL_0033: ldloc.0                                                                    // Load local variable 0
    IL_0034: ldarg.0                                                                    // Load the array (arg 0) onto the stack
    IL_0035: ldloc.1                                                                    // Load local variable 1
    IL_0036: ldelem.i4                                                                  // Load the element on the ->
                                                                                        // arr[local variable 1]
    IL_0037: stelem.i4                                                                  // Replace arr[var 0] with arr[var 1]
    IL_0038: ldarg.0                                                                    // Load the array (arg 0) onto the stack
    IL_0039: ldloc.1                                                                    // Load local variable 1
    IL_003a: ldloc.2                                                                    // Load local variable 2
    IL_003b: stelem.i4                                                                  // Replace arr[var 1] with var 2
    IL_003c: nop                                                                        // Do nothing
    IL_003d: ldloc.0                                                                    // Load local variable 0
    IL_003e: ldc.i4.1                                                                   // Push 1 to the stack
    IL_003f: add                                                                        // Add 1 to the var 0
    IL_0040: stloc.0                                                                    // Store the result in local variable 0

    IL_0041: ldloc.0                                                                    // Load local variable 0
    IL_0042: ldarg.0                                                                    // Load array (arg 0) onto the stack
    IL_0043: ldlen                                                                      // Push the length of the array to the stack
    IL_0044: conv.i4                                                                    // Convert to int32
    IL_0045: clt                                                                        // Compare the two variables. Push 1 if ->
                                                                                        // variable 0 < length of the array
    IL_0047: stloc.s 6                                                                  // Store result in local variable 6
    IL_0049: ldloc.s 6                                                                  // Load local variable 6
    IL_004b: brtrue.s IL_0005                                                           // Jump to IL_0005 if local variable 6 != 0
// end loop

IL_004d: ret                                                                            // return
```

#### (ii - Java)
```
0: iconst_0             // Push 0 onto the stack

1: istore_1             // Pop the top value off the stack (0) and store it in local variable 1 

2: iload_1              // Load local variable 1 onto the stack

3: aload_0              // Load a reference onto the stack from local variable 0 (the array)

4: arraylength          // Get the length of the array

5: if_icmpge     57     // If the length of the array is greater than or equal to the value in local variable 1, jump to line 57

8: iload_1              // Load local variable 1 onto the stack 

9: istore_2             // Pop the top value off the stack and store it in local variable 2 

10: iload_1             // Load local variable 1 onto the stack 

11: iconst_1            // Push 1 onto the stack

12: iadd                // Pop the top two values off the stack, add them, and push the result onto the stack (1+var1)

13: istore_3            // Pop the top value off the stack and store it in local variable 3 

14: iload_3             // Load local variable 3 onto the stack 

15: aload_0             // Load a reference onto the stack from local variable 0 (the array)

16: arraylength         // Get the length of the array

17: if_icmpge     37    // If the length of the array is greater than or equal to the value in local variable 3, jump to line 37

20: aload_0             // Load the array reference onto the stack (the array)

21: iload_3             // Load local variable 3 onto the stack 

22: iaload              // Load the integer arr[var3] from the array onto the stack  

23: aload_0             // Load the array reference onto the stack 

24: iload_2             // Load local variable 2 onto the stack

25: iaload              // Load an integer from the array onto the stack 

26: if_icmpge     31    // If the value in local variable 3 is greater than or equal to the value in local variable 2, jump to line 31

29: iload_3             // Load local variable 3 onto the stack

30: istore_2            // Pop the top value off the stack and store it in local variable 2

31: iinc          3, 1  // Increment local variable 3 by 1

34: goto          14    // Jump to line 14

37: aload_0             // Load the array reference onto the stack

38: iload_1             // Load local variable 1 onto the stack

39: iaload              // Load the integer arr[var1] from the array onto the stack

40: istore_3            // Pop the top value off the stack and store it in local variable 3

41: aload_0             // Load the array reference onto the stack

42: iload_1             // Load local variable 1 onto the stack

43: aload_0             // Load the array reference onto the stack

44: iload_2             // Load local variable 2 onto the stack

45: iaload              // Load the integer arr[var2] from the array onto the stack

46: iastore             // Pop the top two values off the stack and store the second value in the array at the index specified by the first value

47: aload_0             // Load the array reference onto the stack

48: iload_2             // Load local variable 2 onto the stack

49: iload_3             // Load local variable 3 onto the stack

50: iastore             // Pop the top two values off the stack and store the second value in the array at the index specified by the first value

51: iinc          1, 1  // Increment local variable 1 by 1

54: goto          2     // Jump to line 2

57: return
```

### 9.3
The issue in SentinelLockQueue was that the reference to the first item in the queue was not being removed, which caused the program to run out of memory. This is happens since the item can't be properly garbage collected if it isn't de-referenced. 

We fixed the issue by adding the line:
```
    first.next = null;
```
Which can be found on line 104 in QueueWithMistake/QueueWithMistake.java