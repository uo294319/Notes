
---
# Data structures for files management

[Back to index](../README.md)

---
## File Descriptor Block (FDB)

- Stores the information needed by the OS to manage a file.
	- Can also be a folder
	- ID, location in secondary memory, size, protection...
- Stores no actual information of the file.
- All FDB are usually stored at the beginning of the filesystem.
- Only opened files are at the MM.

---
## System open file table

- One for the whole system.
- Stores information about the opened files.
	- Copy of the FDB (actual copy or pointer to the FDB table)
	- Reading/writing pointer (pointer to a R/W memory position)
	-  \# processes sharing (-1 if no sharing)
- New entry is always created if:
	- Different file (FDB)
	- Same file but R/W pointers are not shared.
	- Same file but different mode.
- Opening modes: read (R), write (R) or read/write (R/W)

---
## FDB table in the M.M.

- One for the whole system.
- Contains a copy in MM of the opened files FDB.
	- Also contains the number of references to it.
	- If this number reaches 0 the entry is freed.
- Avoids storing several copies of the same FDB in MM.
- Not every OS implements it.


---
## Process’ open file table

- Stores information about about files opened by each process.
- Stored in MM.
- Contains:
	- pointer to system open file table
	- Can also store R/W pointer.

---
## System calls for files management

### Create file
1. Create a new FDB.
2. Set initial values in the FDB.
### Delete file
- File and its FDB are removed.
### Open file
- If not shared:  `open(<MODE>, <FILE>, 0)`
	1. New entry in open file table (# shared = -1)
	2. Modify the FDB table (if exists)
		- If entry exists increment reference counter.
		- If not exists FDB is copied and reference counter = 1.
		- Set pointer of the entry in step 1 to this.
	3. New entry in process' open file table (File descriptor)
- If shared: `open(<MODE>, <FILE>, 1)`
	- If there is already an entry in open file table:
		1. Increment shared count field.
		2. New entry in the process open file table (File descriptor).
	- If not entry in open file table:
		1. Create an entry with shared count set to 1.
		2. Modify the FDB table (if exists)
			- If entry exists increment reference counter.
			- If not exists FDB is copied and reference counter = 1.
			- Set pointer of the entry in step 1 to this.
		3. New entry in the process open file table (File descriptor).
### Close file
- If not shared:
	1. Entry in open file table is freed.
	2. If there is a FDB table:
		- Decrement the references counter.
		- If counter reaches 0, entry is freed.
	3. Entry in process' open file table is freed.
- If shared:
	1. Entry in open file table is modified:
		- Decrement the shared counter.
		- If counter reaches 0, entry is freed.
	1. Entry in process' open file table is freed.
### Other
- Read/Write
- Append
- Locate
- Rename
---
## System calls for directories management
### Create folder
- FDB are assigned and attributes and special folders (`.`and `..`) are set.
### Link & Unlink
- Create or remove inputs from the directory.
### Other
- Open/close
- Delete
- Rename
- Read
---
