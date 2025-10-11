
---
# File system implementation

[Back to index](../README.md)

---
## File system structure

- A file system is a way of organizing files in the secondary memory (SM).
- Disk is divided in:
	- MBR (lower disk positions)
	- Partition table (just after MBR)
	- Several partitions each with a file system (can be de same or not). 
- Each file system has its own format:
	- Boot block, super block, free space management, root directory...
	- Block size may vary (1kB to 4KB normally).

---
## File implementation

- Files are stored in data blocks in SM.
- Data blocks of the same file may not be adjacent.
- To access them in order there are several implementation.
### Linked List Assignation
- FDB contains only the block number (address) of the file's first block.
- Each block contains the block number of that file's next block.
- Problems:
	- Inefficient direct access, only sequential.
	- Space waste in each block.
### Linked List Assignation using a Table
- There is a table that contains:
	- One entry per block (index = block number)
	- For each entry the block number of the block of a file.
- Advantages:
	- Easier direct access.
	- Whole block used for data.
	- Faster if all table is loaded to MM.
### Indexed assignation
- FDB contains a fixed number of block numbers.
- Some of this blocks contain other block numbers (indirect access).
- Problems:
	- Limited file size. by the index.
	- Access time depends on indirection level.

---
## Folder implementation

- FDB must be reachable by its name.
### MS-DOS Implementation:
- File name (8B)
- Extension (3B)
- Attributes (1B)
- Reserved (10B)
- Time (2B) & Date (2B)
- First block number (2B)
- Size (4B)
### UNIX Implementation:
- FDB resides in a specific area and is called i-node.
- Each i-node is identified by a integer (file ID).
- i-node example:
	- i-node number (2B)
	- File name (14B)

---
## Free space management

- We must know which blocks are free.
### Linked List
- Each free block stores the block number of the next free block.
- Only the block number of the first block is required.

### Bits Map
- We need a sequence of bits, one per block.
- Each bit is `1` if the block is free or `0` if used.
- Easy to find consecutive free blocks.

---
## File system consistency

- Operations over files and data structures take place in the MM.
- The system can fail before writing information to the disk:
	- File system can be in an inconsistent state.
	- Critical if FDB, folders or free block structure loss information.
- OS must be able to check consistency of the file system with utilities:
### Check Consistency with `fsck`
- **Block consistency**:
	- Goes block by block creating two tables (initially set to `0`).
		- One stores the number of times a block belongs to a file.
		- The other stores the number of times a block appears as free.
	- For each position in the tables, one must be `1` and the other `0`.
		- If both are `0` a the block was lost.
		- If there is a number greater than `1` the block is replicated.
- **Directories consistency**:
	2. Creates a counter for each FDB initially set to `0`.
	3. Traverses the folder hierarchy increasing the counter for each reference.
	4. Compares the counter with the number of names in the FDB.
		- If equal they are consistent.
		- If the count is less, some filename was lost.
		- If the counter is greater, we are pointing to a removed file.
	5. Re-adjust the number of names in the FDB using the count.

---