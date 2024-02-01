### Huffman Coding

<pre>
Huffman Coding is a text compression algorithm. It supports variable length codes.

Characters having higher frequency, will have less space(bits) and characters having less frequency, will have more space(bits).

</pre>
### DataStructers for Huffman Coding
<pre>
1. Hash Map - will be used to store character frequency {char:freq}, and 
              also to store code for each character{char:bits}
2. Tree - to define structure of nodes
3. Min Heap - to find 2 min occuring characters at each node
</pre>

### Steps for Huffman Coding
1. Calculate the frequency of each character and store it in a Hashmap.
2. Pick 2 characters with minimum frequency, make a node combining those 2 characters and adding their frequencies, remove those two nodes from the hashmap and repeat the process.

To determine code for each character, starting from the top node, if the character is left child add 0, if it is right child add 1.
<pre>
Suppose, we have the following code for each character,
a -> 00
g -> 01
d -> 11
b -> 101
c -> 1001
x -> 10000
z -> 10001

All these codes will be <b>prefix free code</b>. That is, we have 00 for a, so no other code will start with 00 for any other code. This is because all the character nodes in our tree are child nodes. There are no nodes beneath them.

We can see that, a which has most frequency takes less bits and z which has less frequency takes more bits.

With this code, 
We can compress,
'abadg' to 00101001101.
abadg as string char would have taken 5bytes(1 byte for each char) = 5*8 = 40bits
but, 00101001101 would take only 11 bits which is less than 2 bytes.
</pre>
Thus, we have compressed the text.

### Decompression in Huffman Coding

1. First we need a reverse map of codes and characters.
2. We will start from the left and search for first available key in the reverse map and add the corresponding character to the output and will continue with the rest of the compressed string.

