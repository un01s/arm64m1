# hello.s

```
$objdump -s -d hello.o 

hello.o:	file format mach-o arm64

Contents of section __TEXT,__text:
 0000 200080d2 e1000010 a20180d2 900080d2   ...............
 0010 011000d4 000080d2 300080d2 011000d4  ........0.......
 0020 48656c6c 6f20576f 726c6421 0a        Hello World!.

Disassembly of section __TEXT,__text:

0000000000000000 <ltmp0>:
       0: 20 00 80 d2  	mov	x0, #1
       4: e1 00 00 10  	adr	x1, #28
       8: a2 01 80 d2  	mov	x2, #13
       c: 90 00 80 d2  	mov	x16, #4
      10: 01 10 00 d4  	svc	#0x80
      14: 00 00 80 d2  	mov	x0, #0
      18: 30 00 80 d2  	mov	x16, #1
      1c: 01 10 00 d4  	svc	#0x80

0000000000000020 <helloworld>:
      20: 48 65 6c 6c  	ldnp	d8, d25, [x10, #-320]
      24: 6f 20 57 6f  	umlal2.4s	v15, v3, v7[1]
      28: 72 6c 64 21  	<unknown>
      2c: 0a           	<unknown>
```

