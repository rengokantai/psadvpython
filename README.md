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
```
int(-241).to_bytes(2,byteorder='big') #error
```
```
int(-241).to_bytes(2,byteorder='big',signed=True)
```
```
bin((~0b11110000).to_bytes(2,byteorder='little',signed=True)[0])  #'0b1111'
```

### 4 The Bytes Type in Depth
```
norsk = b"like \xc5 and \xd8 are not 7bit ASCII"
norsk.decode('latin1')
```

```
bytes() #,65+36 b''
bytes(5) # b'\x00'
bytes(range(65,65+26)) #b'ABCD....'
```

```
bytes('norwe','utf16')
# b'..'
```

```
bytes.fromhex('123456789abc')
b''
```
reverse:
```
''.join(hex(c)[2:] for c in b'The quick fox')
```


### 5 The bytearray Type
```
program = bytearray(b'ke')
program.extend(b'y')
```
split and join
```
words = program.split()
bytearray(b' ').join(words)
```


## 4.Object Internals and Custom Attributes
### 2 How are Python Objects Represented?
```
v.Vector(5,3)
v.__dict__
type(v.__dict__)
v.__dict__['x']
del v.__dict__['x']
```
```
'x' in v.__dict__
#false
```

```
getattr(v,'x')
hasattr(v,'x')
delattr(v,'x')
setattr(v,'x',9)
```

###### 03:20
```
class Vector:
  def __init__(self,**coords):
    self.__dict__.update(coords)
  def __repr__(self):
    return "{}({})".format（self.__class__.__name__,','.join("{k}={v}.format(k=k,v=self.__dict__[k]) for k in sorted(self.__dict__.keys())))
```



### 3.Overriding __getattr__
```
__getattr__()  # invoked after requested attribute/property not found by normal lookup
```

```
__getattribute__() # invoked instead of normal lookup
```
