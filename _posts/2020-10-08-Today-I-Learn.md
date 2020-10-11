> Collection of bits of TILs

# Python

## 2020.10.08
Before copying the Python program from dev computer to other computers, extract all the required packages with the command:

* Usage: `pipreqs [options] <path>`
* Example: `pipreqs C:\Users\zj\Desktop\py_program`

This will generate a `requirements.txt` file with all the package names and versions.

In other computers, run the command `pip install -r requirements.txt` to install all the required packages.