
---
# OS Module

[Back to index](../README.md)

---

```python
os.getcwd() # Get current working directory
os.chdir('path') # Change current working directory
os.listdir() # List current working directory

os.mkdir('dir') # Make a directory
os.makedirs('path/dir') # Make a directory (creates sublevels)

os.rmdir('dir') # Remove a directory
os.removedirs('path/dir') # Remove a directory (removes sublevels)

os.rename('olddir', 'newdir') # Rename directory

os.stat('file') # Gives the status (info) of a file

os.walk('path')
# returns a generator of a tree of paths, subdirectories and files

os.eviron.get('env') # Returns the environment path

os.path.join('path', 'path') # Joins the paths in the proper format
os.path.filename('path') # Returns the filename in the path
os.path.dirname('path') # Returns the directory name in the path
os.path.split('path') # Returns the previous two combined
os.path.exists('path') # Returns true if the path exits
os.path.isfile('path') # Returns true if the path is a file
os.path.isdir('path') # Returns true if the path is a directory
os.path.splitext('path') # Split the path and the extension
```

[Python Tutorial: Calling External Commands Using the Subprocess Module (youtube.com)](https://www.youtube.com/watch?v=2Fp1N6dof0Y)