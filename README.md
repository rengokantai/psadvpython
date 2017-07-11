# psadvpython
## 3. Byte-oriented Programming
```
240= +0b11110000 => 011110000  
~240=100001111=>+1 = -0b11110001
```
but in python3
```
-0b11110001=00001110,add1=00001111
```
or
```
-241+15=256
```

Two's complement with bitwise shift
```
def twos_complement(x,num_bits):
  if x<0:
    return x+(1<<num_bits)
  return x
```
```
v
240
~v
-241
two_complement(~v,8)
15
bin(_)
0b1111
```

```
# eight 1's
bin(~0b11110000 & 0b11111111)
0b1111
```

```
# nine 1's
bin(~0b11110000 & 0b111111111)
0b100001111
```

```
int(32).bit_length()
```

```
int(0xcaf).to_bytes(length=4,byteorder='big')
int(0xcaf).to_bytes(length=4,byteorder='little')
```
```
import sys
sys.byteorder
#'little'
```
```
little = int(0xabcd).to_bytes(length=4,byteorder=sys.byteorder)
```
```
int.from_bytes(little,byteorder=sys.byteorder)
```
int.from_bytes(little
