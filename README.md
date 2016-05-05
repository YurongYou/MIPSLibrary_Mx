This code is served as a built-in function library of Mx Language of Compiler Project of ACM Honored Class

Built by Ficos 16/5/2
All rights reserved.

All test passed.
## Update(16/5/5)
1. fix a bug in `func_parseInt`, where the previous version cannot parse negative integer (but this situation does not appear in any test cases)
2. add `func__stringLeq`, `func__stringGeq`, `func__stringNeq` and `func__stringLarge`
3. Now when calling `func_toString` and `func_stringConcatenate` you don't need to save any register other than `$v0`, `$v1`(if you used them)
4. you **don't** need to call "`_buffer_init`" function before entering the source main function!!!

## Note:
1.`func_getInt` will read input until `\n`, for I call MIPS sysfunc indeed.
## Usage:

1. Just paste all of this in front of your MIPS code

### All supported functions:

		FunctionName	|		args
		--------------|--------
1.	func_print 				|`$a0`: the string
2.	func_println			|`$a0`: the string
3.	func_getString			|---
4.	func_getInt				|---
5.	func_toString			|`$a0`: the integer
6.	func_string.length 	|`$a0`: the string
7.	func_string.substring |  `$a0`: the string,  `$a1`: left pos(int), `$a2`: right pos(int)
8.	func_string.parseInt |`$a0`: the string
9.	func_string.ord 		|`$a0`: the string,  `$a1`: pos(int)
10.	func__array.size 	|`$a0`: the array
11.	func_stringConcatenate |	`$a0`: left string, `$a1`: right string
12.	func_stringIsEqual 	|	`$a0`: left string, `$a1`: right string
13.	func_stringLess 	|	`$a0`: left string, `$a1`: right string
14.	func__stringLeq	| 		`$a0`: left string, `$a1`: right string
15.	func__stringGeq	| 		`$a0`: left string, `$a1`: right string
16.	func__stringNeq	|		`$a0`: left string, `$a1`: right string
17.	func__stringLarge 	|	`$a0`: left string, `$a1`: right string

## Calling Conventions:
1. args placed in `$a0`, `$a1`, `$a2`
2. return in `$v0`
3. follow the MIPS calling convention, **be careful on regs when calling these functions**
4. all used regs are presented in the front of the function

## Conventions in using string:
1. string object is simply a register contains the initial address of the string
2. front of every initial address of a string are a word containing the length of the string
   e.g.

		   .data
		 		  .word 6
			 str: .asciiz "hello\n"
				  .align 2
	
3. every string ends with `'\0'`, which is not counted in the length

## Conventions in using array:
1. front of every initial address of a array are a word containing the size of the array


