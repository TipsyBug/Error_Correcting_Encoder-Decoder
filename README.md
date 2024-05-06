# Error Correcting Encoder-Decoder

Java Project @JetBrains Academy

A program is designed to encode and decode text messages with error detection and correction capabilities during data transmission. It accomplishes the following tasks:

- Encoding: Converts text messages into a bit sequence using a specific encoding method, such as the Hamming code. This process adds redundancy to the data, allowing errors to be detected and corrected later.
- Decoding: Transforms the encoded bit sequence back into its original text form, correcting any errors encountered during transmission.
- Error Correction: The program can identify and correct errors in the encoded data, using the redundancy introduced during the encoding phase. This ensures that the decoded output matches the original input, even if the data has been corrupted.
- Input and Output Processing: It can process various data formats, including hexadecimal, binary, and text, to encode and decode messages.

This program serves as an example of how error correction algorithms can be implemented in a simple application, demonstrating the principles of error detection and correction in data communication systems. It allows users to understand the basics of error correction and how it can be applied to maintain data integrity.

## Prerequisites

This program requires Java to compile and run.

## Installation

- Download this repository and unzip the .zip file in your desired location.
- Open a terminal, then enter ```cd "Error Correcting Encoder-Decoder/task/src"```.
- Compile the program using the command ```javac correcter\Main.java```.
- Run the program using the command ```java correcter.Main```.

## Example of use

The program reads the text the user wants to send from the send.txt and simulates its posting through a poor internet connection by making one-bit errors in every byte of the text.

For that, the program implements a Hamming code. In this code, every byte contains 4 significant bits, and the other 4 bits are used as an overhead (to be more precise, since the last one just isn't used, only 3 of them are used as an overhead).

MODES:
- "encode": text from an input file is converted to a ready-to-send form (where you have three significant bits per byte). The resulting bytes are then saved into a (different) output file.
- "send": generates errors in the bytes (1 bit per byte) of a text file and saves the resulting bytes into another file.
- "decode": an encoded input file is decoded back into normal text which is then saved to an output file.

The symbol > represents the user input. Notice that it's not the part of the input.

```> java correcter.Main```

Encode mode
```
Write a mode: > encode

send.txt:
text view: Test
hex view: 54 65 73 74
bin view: 01010100 01100101 01110011 01110100

encoded.txt:
expand: ..0.101. ..0.100. ..0.110. ..0.101. ..0.111. ..0.011. ..0.111. ..0.100.
parity: 01001010 10011000 11001100 01001010 00011110 10000110 00011110 10011000
hex view: 4A 98 CC 4A 1E 86 1E 98
```

Send mode
```
Write a mode: > send

encoded.txt:
hex view: 4A 98 CC 4A 1E 86 1E 98
bin view: 01001010 10011000 11001100 01001010 00011110 10000110 00011110 10011000

received.txt:
bin view: 01001000 10011100 11001000 01001000 00011111 10000010 00001110 10111000
hex view: 48 9C C8 48 1F 82 0E B8
```

Decode mode
```
Write a mode: > decode

received.txt:
hex view: 48 9C C8 48 1F 82 0E B8
bin view: 01001000 10011100 11001000 01001000 00011111 10000010 00001110 10111000

decoded.txt:
correct: 01001010 10011000 11001100 01001010 00011110 10000110 00011110 10011000
decode: 01010100 01100101 01110011 01110100
hex view: 54 65 73 74

text view: Test
```
