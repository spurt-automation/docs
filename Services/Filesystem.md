# Filesystem Service
The filesystem service is the interface between Spurt and the filesystem.
It allows reading and writing files, as well as scanning folders.

## Steps
### Files In Folder
This step scans a folder for its files and returns a list of them.

## Resources
### File Resource
The file resource is a generic resource that handles files. It is extended by image resource.

### Folder Resource
The folder resource handles a folder on the filesystem. It wraps the File class from java.io.

### Image Resource
The image resource is a specific type of file. Currently it has no extra functionality, but will have in the future.


