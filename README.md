# io
Universal IO UTF-8 Encodes bytes as specificated into charCodes that are 1:1 byte streams when there is no offical charcode it adds the original byte with 0xFF the UTF-8 Private address space so when you drop that from the sequence of bytes that your getting your getting rawBytes as u8 Int array. 

## use ECMAScript / JavaScript / Typescript
All Strings in ECMAScript and based languages are u8 integer Arrays containing charCodes that get represented as String Charakters when parsed
as Utf8 has the concept of codePoints which can include 1 or 2 chars as of time of writing. 
```ts
const myString = "string" // every string is a utf8 encoded UInt8 array so we deal with integers streamed
// Hexadecimal is the name of the numbering system that is base 16. This system, therefore, 
// has numerals 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, and 15
function hexColour(c) {
  // a UInt8 Array holds numbers between 0-255 which represent charCodes
  if (c < 256) {
    return Math.abs(c).toString(16); // represent with radix other word for base 16 
  }
  return 0;
}

console.log(hexColour(233)); // => "e9"
console.log(hexColour('11')); // => "b"


// CodePoints if you parse for example as UInt16 you get 1 or two Chars out of that numbers with UInt32 you can get charCodes 4 times u8 elements.

'ABC'.codePointAt(0)                        // 65
'ABC'.codePointAt(0).toString(16)           // 41 // Hex

'😍'.codePointAt(0)                         // 128525
'\ud83d\ude0d'.codePointAt(0)               // 128525
'\ud83d\ude0d'.codePointAt(0).toString(16)  // 1f60d // Hex

'😍'.codePointAt(1)                         // 56845
'\ud83d\ude0d'.codePointAt(1)               // 56845
'\ud83d\ude0d'.codePointAt(1).toString(16)  // de0d // Hex

'ABC'.codePointAt(42)                       // undefined
```



## use java
Convert a list of UTF-8 numbers to a normal String
decoding a message that is delivered as a sequence of bytes instead of plain text via stdio

```java
public String convertUtf8NumbersToString(String[] numbers){
    int length = numbers.length;
    byte[] data = new byte[length]; // sharedArrayBuffer

    for(int i = 0; i< length; i++){
        data[i] = Byte.parseByte(numbers[i]);
    }
    return new String(data, Charset.forName("UTF-8"));
}
```


Convert from String to byte[]:
```java
String s = "some text here";
byte[] b = s.getBytes(StandardCharsets.UTF_8);
```

Convert from byte[] to String:
```java
byte[] b = {(byte) 99, (byte)97, (byte)116};
String s = new String(b, StandardCharsets.US_ASCII);
```
