# File Manipulation / System.IO



## File and stream I/O (input/output) 
Refers to the transfer of data either to or from a storage medium. In .NET, the System.IO namespaces contain types that enable reading and writing, both synchronously and asynchronously, on data streams and files.




### Some commonly used file and directory classes:

- File - provides static methods for creating, copying, deleting, moving, and opening files, and helps create a FileStream object.

- FileInfo - provides instance methods for creating, copying, deleting, moving, and opening files, and helps create a FileStream object.

- Directory - provides static methods for creating, moving, and enumerating through directories and subdirectories.

- DirectoryInfo - provides instance methods for creating, moving, and enumerating through directories and subdirectories.

- Path - provides methods and properties for processing directory strings in a cross-platform manner.



### Isolated storage

Isolated storage is a data storage mechanism that provides isolation and safety by defining standardized ways of associating code with saved data.



### How to: Write text to a file ?


The following classes and methods are typically used to write text to a file:



- StreamWriter: contains methods to write to a file synchronously (Write and WriteLine) or asynchronously (WriteAsync and WriteLineAsync).

- File: provides static methods to write text to a file, such as WriteAllLines and WriteAllText, or to append text to a file, such as AppendAllLines, AppendAllText, and AppendText.

- Path: is for strings that have file or directory path information. It contains the Combine method and, in .NET Core 2.1 and later, the Join and TryJoin methods, which allow concatenation of strings to build a file or directory path.

### How to: Read and write to a newly created data file ?

- The System.IO.BinaryWriter and System.IO.BinaryReader classes are used for writing and reading data other than character strings.


