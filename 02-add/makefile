addexample: addexample.o
	ld -o addexample addexample.o -lSystem -syslibroot `xcrun -sdk macosx --show-sdk-path` -e _start -arch arm64 

addexample.o: addexample.s
	as -arch arm64 -o addexample.o addexample.s
