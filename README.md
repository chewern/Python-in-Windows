# Running Python in Windows 10 environment

The purpose of this repository is to document the solution to fix the problem of `python` command not 
found in Git Bash and/or Windows Powershell. Apparently this problem is rather common because I faced
the same issue in at least 3 new Windows 10 laptops from 3 different brands. 

1.  Check if python.exe is installed in the computer. Locate the directory that holds the python.exe
and related files (it may be kept in hidden folder). Note down this directory.

2.  Use Notepad (or any text editor) create a new file with this name: `.profile` and save it in your 
Windows 10 user's root directory, which is typically `C:\Users\{your windows user name}`

3.  Within the `.profile` file, type in the following:  
      `PATH="{full path to your python.exe file}:$PATH"`  
      `PATH="{full path to pip.exe}:$PATH"`  
      
    As an example, my entries would be the following:  
      `PATH="C:\Users\chewern\AppData\Local\Programs\Python\Python38:$PATH"`  
      `PATH="C:\Users\chewern\AppData\Local\Programs\Python\Python38\Scripts:$PATH"`

4.  Save and close `.profile` file. Then close and re-open Git Bash, type `python --version` to check if 
Windows 10 can now find the path to python.exe.

5.  What happened is that somehow Windows 10 messed up the path for Python, such that Git Bash does not find
python.exe and pip.exe. As such you have to manually specify a path for Git Bash using the special `.profile` file.
Whenever Git Bash starts up, it will find the `.profile` file in the Windows user's root directory for extra 
instructions on paths.

6.  (Optional) Send a complaint email to Microsoft asking why Windows 10 doesn't find python.exe in Git Bash.
