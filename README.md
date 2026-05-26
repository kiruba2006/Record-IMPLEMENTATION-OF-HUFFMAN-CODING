# EX NO – 11  
# IMPLEMENTATION OF HUFFMAN CODING

---

# Aim

To implement Huffman Coding using Python for generating variable-length binary codes based on the frequency of characters in a given string.

---

# Software Required

- Anaconda – Python 3.7  
- Python IDLE / Jupyter Notebook  

---

# Algorithm

### Step 1:
Start the program.

### Step 2:
Read the input string.

### Step 3:
Calculate the frequency of each character in the string.

### Step 4:
Create nodes for every character with its frequency.

### Step 5:
Sort the nodes based on frequency in ascending order.

### Step 6:
Select the two nodes with the smallest frequencies.

### Step 7:
Combine them into a new node with the sum of frequencies.

### Step 8:
Insert the new node back into the list.

### Step 9:
Repeat the process until only one node remains.

### Step 10:
The remaining node becomes the Huffman Tree.

### Step 11:
Traverse the Huffman Tree:
- Assign 0 for the left branch.
- Assign 1 for the right branch.

### Step 12:
Generate Huffman codes for all characters.

### Step 13:
Display the character and its corresponding Huffman code.

### Step 14:
Stop the program.

---

# Program

### Developed By : Kiruba RC
### Register Number : 212224230125

```python
# Get the input String
input_string = "Kiruba"

# Calculate frequency of each character
frequency = {}

for char in input_string:
    if char in frequency:
        frequency[char] += 1
    else:
        frequency[char] = 1

# Create tree nodes
nodes = [[char, freq] for char, freq in frequency.items()]

# Main function to implement Huffman Coding
while len(nodes) > 1:

    # Sort nodes based on frequency
    nodes = sorted(nodes, key=lambda x: x[1])

    # Pick two smallest nodes
    left = nodes.pop(0)
    right = nodes.pop(0)

    # Create new node with combined frequency
    new_node = [[left, right], left[1] + right[1]]

    nodes.append(new_node)

# Final Huffman Tree
huffman_tree = nodes[0]

# Dictionary to store Huffman codes
huffman_codes = {}

# Function to generate codes
def generate_codes(tree, code=""):

    # Leaf node
    if isinstance(tree[0], str):
        huffman_codes[tree[0]] = code

    # Internal node
    else:
        generate_codes(tree[0][0], code + "0")
        generate_codes(tree[0][1], code + "1")

# Generate Huffman Codes
generate_codes(huffman_tree)

# Display Huffman Codes
print("Character | Huffman Code")
print("-------------------------")

for char, code in huffman_codes.items():
    print(f"    {char}    |    {code}")
```

---

# Output

## Huffman Codes Generated

<img width="299" height="200" alt="image" src="https://github.com/user-attachments/assets/9c61572a-4cdb-462b-bc03-5bf5423f719b" />


---


# Result

Thus the Huffman Coding algorithm was successfully implemented using Python. The program generated Huffman codes for each character in the input string based on their frequencies and displayed the corresponding binary codes successfully.
