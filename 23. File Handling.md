# FILE MANAGEMENT

---

# What is File Management?

File Management means using Python to create, read, update, and delete files stored on disk.

Files provide **permanent storage**.

Without files:

Program Starts
↓
Data stored in RAM
↓
Program Ends
↓
Data Lost

With files:

Program Starts
↓
Data written to Disk
↓
Program Ends
↓
Data Still Exists

Examples:
- Saving user details
- Application logs
- Configuration files
- CSV reports
- Text documents

---

# File Operation Lifecycle

Every file operation follows:

OPEN
↓
READ / WRITE / APPEND
↓
CLOSE

Example:

test.txt
↓
open()
↓
perform operations
↓
close()

---

# Opening Files

Syntax:

```python
fileobj = open(filename, mode)
```

Example:

```python
fileobj = open("test.txt")
```

Default mode:

```python
open("test.txt")
```

is equivalent to:

```python
open("test.txt", "r")
```

---

# File Modes

| Mode | Purpose | File Exists? | Cursor Position |
|--------|----------|--------------|------------------|
| `"r"` | Read | Must exist | Beginning |
| `"w"` | Write | Creates/Overwrites | Beginning |
| `"a"` | Append | Creates if absent | End |
| `"r+"` | Read + Write | Must exist | Beginning |
| `"w+"` | Read + Write | Creates/Overwrites | Beginning |
| `"a+"` | Read + Append | Creates if absent | End |

---

# Read Mode ("r")

Purpose:

Read existing data.

Example:

```python
fileobj = open("test.txt", "r")
```

Flow:

File Exists
↓
Open Successfully
↓
Read Contents

If file doesn't exist:

```python
FileNotFoundError
```

---

# Write Mode ("w")

Purpose:

Write new data.

Example:

```python
fileobj = open("test.txt", "w")
```

Behavior:

File Exists
↓
Delete old contents
↓
Write new contents

OR

File Doesn't Exist
↓
Create New File

Example:

```python
fileobj.write("Hello")
```

Result:

Before:

```
Python
Java
```

After:

```
Hello
```

Old data is lost.

---

# Append Mode ("a")

Purpose:

Add data without deleting existing data.

Example:

```python
fileobj = open("test.txt", "a")
fileobj.write("New Line")
```

Flow:

Existing Content
↓
Cursor moves to end
↓
New data added

Before:

```
Hello
```

After:

```
Hello
New Line
```

---

# Closing Files

Syntax:

```python
fileobj.close()
```

Example:

```python
fileobj = open("test.txt")
fileobj.close()
```

Why close?

- Releases system resources
- Saves buffered data
- Prevents file corruption
- Avoids memory leaks

Lifecycle:

Open
↓
Use
↓
Close

---

# Reading Entire File

Syntax:

```python
fileobj.read()
```

Example:

```python
fileobj = open("test.txt")
print(fileobj.read())
```

Suppose file contains:

```
Line1
Line2
Line3
```

Output:

```
Line1
Line2
Line3
```

---

# File Cursor

File cursor indicates current reading/writing position.

Example:

```
Python File

^
Cursor starts here
```

After:

```python
fileobj.read()
```

Cursor becomes:

```
Python File
           ^
         End
```

---

# Why Second read() Returns Empty?

Example:

```python
fileobj.read()
fileobj.read()
```

Output:

```python
'contents'
''
```

Reason:

First read():

Beginning
↓
Reads entire file
↓
Cursor reaches end

Second read():

Cursor already at end
↓
Nothing left to read

---

# seek()

Purpose:

Move cursor to a specific location.

Syntax:

```python
fileobj.seek(position)
```

Example:

```python
fileobj.seek(0)
```

Cursor:

Beginning

Example:

```python
fileobj.seek(7)
```

Cursor moves to position 7.

Example:

```python
fileobj.seek(0)
print(fileobj.read())
```

---

# tell()

Purpose:

Get current cursor position.

Syntax:

```python
fileobj.tell()
```

Example:

```python
fileobj.seek(0)
fileobj.read(16)

print(fileobj.tell())
```

Output:

```python
16
```

Flow:

Start
↓
Read 16 characters
↓
Cursor at 16

---

# Reading Specific Characters

Example:

```python
fileobj.seek(0)
print(fileobj.read(16))
```

Suppose file contains:

```
Python generators are easy...
```

Output:

```python
Python generator
```

Only first 16 characters are returned.

---

# readline()

Purpose:

Read one line at a time.

Syntax:

```python
fileobj.readline()
```

Example:

```python
fileobj.seek(0)

print(fileobj.readline())
print(fileobj.readline())
```

Output:

```
First Line
Second Line
```

Flow:

Line 1
↓
Cursor moves
↓
Line 2
↓
Cursor moves

---

# readlines()

Purpose:

Read all lines as a list.

Syntax:

```python
fileobj.readlines()
```

Example:

```python
fileobj.seek(0)

print(fileobj.readlines())
```

Output:

```python
[
    'First Line\n',
    'Second Line\n',
    'Third Line\n'
]
```

---

# Reading First N Lines

Using readline():

```python
fileobj.seek(0)

for i in range(5):
    print(fileobj.readline())
```

Output:

First five lines.

---

Using readlines():

```python
fileobj.seek(0)

count = 0

for line in fileobj.readlines():
    if count < 5:
        print(line)
    else:
        break

    count += 1
```

Output:

First five lines.

---

# Writing to Files

Syntax:

```python
fileobj.write(data)
```

Example:

```python
fileobj = open("test.txt", "a")

fileobj.write("NEW CONTENT")

fileobj.close()
```

Behavior:

Existing Data
↓
Append New Data

---

# Overwriting Files

Example:

```python
fileobj = open("test.txt", "w")

fileobj.write(
    "NEW CONTENT ADDED IN THE FILE"
)

fileobj.close()
```

Behavior:

Old Content
↓
Deleted
↓
New Content Stored

---

# Creating New Files

Example:

```python
fileobj = open("test2.txt", "w")

fileobj.write("First Line\n")
fileobj.write("Second Line\n")
fileobj.write("Third Line\n")

fileobj.close()
```

Result:

test2.txt

```
First Line
Second Line
Third Line
```

---

# Deleting Files

Import:

```python
import os
```

Delete:

```python
os.remove("test3.txt")
```

Flow:

File Exists
↓
Deleted

If file doesn't exist:

```python
FileNotFoundError
```

Example:

```python
os.remove("test3.txt")
```

Output:

```python
FileNotFoundError
```

---

# Deleting Folders

Syntax:

```python
os.rmdir("folder1")
```

Flow:

Folder Exists
↓
Folder Empty
↓
Deleted

If folder doesn't exist:

```python
FileNotFoundError
```

Example:

```python
os.rmdir("folder1")
```

---

# Safe File Handling (Recommended)

Instead of:

```python
fileobj = open("test.txt")

# operations

fileobj.close()
```

Use:

```python
with open("test.txt", "r") as fileobj:
    print(fileobj.read())
```

Flow:

Open
↓
Execute Block
↓
Automatically Close

Advantages:
- Cleaner syntax
- Prevents forgetting close()
- Handles exceptions safely

---

# Complete Mental Model

Files
↓
open()
↓
Choose Mode
↓
Read / Write / Append
↓
Cursor Moves
↓
seek() / tell()
↓
close()

Recommended:

with open(...)
↓
Automatic close()
↓
Safer File Handling
