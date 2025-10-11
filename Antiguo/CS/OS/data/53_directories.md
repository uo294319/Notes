
---
# Directories

[Back to index](../README.md)

---
## Introduction

- Directories are considered a type of file in some OSs.
- Grant a correspondence between files and a name
	- Contain several relations to files in the folder.
	- Relation present in the File Descriptor Block (FDB)

---
## Hierarchical directories system

- Each folder contains pointers to other files and folders.
	- Tree structure (hierarchical)
	- Structure defined by de user.
- **Absolute paths**
	- Sequence of folders from the tree root to a specific location.
- **Relative paths**
	- The working directory is the directory a user is currently in.
	- `.` represents the current working directory.
	- `..` represents the directory immediately above the working one.