# Hashtables
A data structure that can store with a key and value. Similar to an object.

### Hash
The result of an algorithm taking in an incoming string and altering it into a value for other purposes (hashing for authentication).
### Buckets
What is contained in each index of the array of the hashtable. Each index is a bucket which could potentially contain multiple key/value pairs if a collision occurs.
### Collisions
An event when more than one key gets hashed into the same location of the hashtable.   

* Hash maps have an O(1) time of read access.

## Structure
### Hashing
A hash code turns a key into an integer. It is essential that the same key should result into the same integer. 

### Create a Hash
There should be a specific logic in turning a key into a numeric value.
#### Example
1. add/multiply all the ASCII value
2. multiply by a prime number
3. use modulo to get the remainder of the result when divided by the total size of the array
4. insert into array at that index
```
Key = "Cat"
Value = "Josie"

67 + 97 + 116 = 280

280 * 599 = 69648

69648 % 1024 = 16

Key gets placed in index of 16. 
```
### Collisions
Collisions occur when more than one key hashes to the same index in an array. Best case each key has its own unique index. The worst is where all keys are in the same index. 
Collisions can be solved by changing the initial state of the buckets. This can be done by initializing a linked index in each bucket. When two keys are in the same index, 
the key/value pairs can be stored in as a node in a linked list.  
In order to solve less collisions it is ideal to have numerous buckets. However, this can also mean wasting space with empty buckets. So it is always important to balance 
with the size and collision possibility.

## Internal Methods
### Add()
- adding a newkey/value
1. send the key to the `GetHash` method
2. once determined the index of where it should go, go to the index
3. check if index is already taken, if not add it with key/value pair
4. if taken, add new key/value pair to the data structure within bucket (linked list?)

### Find()
takes in a key, gets the hash and goes to the index location of specified. => once at index location, iterates over data structure of bucket to find if key exists and return value

### Contains()
accpets a key and return a boolean if the key exists in hashtable => ideally `contains` calls `GetHash` and check hashtable if key exsits in table

### GetHash()
accepts key as a string conduct hash and return the index of the array where key/value should be placed.

