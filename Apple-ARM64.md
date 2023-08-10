# ARM64 assembly on Apple silicon M1/M2

## Differences Between MacOS and Linux

Both MacOS and Linux are based on Unix and are more similar than different. However there are a few differences of note:

* MacOS uses LLVM by default whereas Linux uses GNU GCC. This really just affects the command line arguments in the makefile for the purposes of this article. You can use LLVM on Linux and GCC should be available for Apple M1 shortly.

* The MacOS linker/loader doesn’t like doing relocations, so you need to use the ADR rather than LDR instruction to load addresses. You could use ADR in Linux and if you do this it will work in both.

* The Unix API calls are nearly the same, the difference is that Linux redid the function numbers when they went to 64-bit, but MacOS kept the function numbers the same. In the 32-bit world they were the same, but now they are all different.

* When calling a Linux service the function number goes in X16 rather than X8.

* Linux installs the various libraries and includes files under /usr/lib and /usr/include, so they are easy to find and use. When you install XCode, it installs SDKs for MacOS, iOS, iPadOS, iWatchOS, etc. with the option of installing lots for versions. The paths to the libs and includes are rather complicated and you need a tool to find them.

* In MacOS the program must start on a 64-bit boundary, hence the listing has an “.align 2” directive near top.

* In MacOS you need to link in the System library even if you don’t make a system call from it or you get a linker error. This sample Hello World program uses software interrupts to make the system calls rather than the API in the System library and so shouldn’t need to link to it.

* In MacOS the default entry point is _main whereas in Linux it is _start. This is changed via a command line argument to the linker.

## specific registers

* x18 is reserved. Don't use it.
* frame pointer register x29 must always addresses a valid frame record.

## data type alignment

* wchar_t type 32-bit, signed
* char type, a signed type
* __fp16 type uses IEEE754-2008 format
* long double type is a double precision IEEE754 binary floating-point type

## reference

* [Stephen Smith's blog](https://smist08.wordpress.com/2021/01/08/apple-m1-assembly-language-hello-world/)

* [apple arm64](https://developer.apple.com/documentation/xcode/writing-arm64-code-for-apple-platforms)
