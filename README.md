# MemLabs Solutions

This is solutions of famous memory forensics challenge [MemLabs](https://github.com/stuxnet999/MemLabs).

## MemLabs Lab 0

#### Use the following commands to acquire flag

```bash
volatility -f Challenge.raw imageinfo
volatility -f Challenge.raw --profile=Win7SP1x86 pslist
volatility -f Challenge.raw --profile=Win7SP1x86 cmdscan
volatility -f Challenge.raw --profile=Win7SP1x86 consoles
volatility -f Challenge.raw --profile=Win7SP1x86 envars
volatility -f Challenge.raw --profile=Win7SP1x86 hashdump
```
Flag: flag{you_are_good_but1_4m_b3tt3r}

## MemLabs Lab 1

#### Use the following commands to acquire 1st flag

```bash
# Detect version of OS
volatility -f MemoryDump_Lab1.raw imageinfo
# List all running processes
volatility -f MemoryDump_Lab1.raw --profile=Win7SP1x86 pslist
# List all executed CMDlets
volatility -f MemoryDump_Lab1.raw --profile=Win7SP1x86 cmdscan
# List all stdout
volatility -f MemoryDump_Lab1.raw --profile=Win7SP1x86 consoles
```
Flag encoded: ZmxhZ3t0aDFzXzFzX3RoM18xc3Rfc3Q0ZzMhIX0=

Flag: flag{th1s_1s_th3_1st_st4g3!!}

#### Use the following commands to acquire 2nd flag

```bash
# Find PID of mspaint
volatility2 -f MemoryDump_Lab1.raw --profile=Win7SP1x64 pslist
# Dump run process to a file
volatility2 -f MemoryDump_Lab1.raw --profile=Win7SP1x64 memdump -p 2424 -D paint/
# Change extension of file
mv 2424.raw 2424.data
# Open 2424.data file on GIMP
gimp 2424.data
```
###### Adjust width and height of image for reveal 2nd flag
![App Screenshot](images/lab1_flag2.png)
![App Screenshot](images/lab1_flag2-ext.png)

#### Use the following commands to acquire 3rd flag

```bash
# List files that loaded to RAM. We only need Alissa's files
volatility2 -f MemoryDump_Lab1.raw --profile=Win7SP1x64 filescan | grep "Alissa Simpson"
# Dump important.rar file
volatility2 -f MemoryDump_Lab1.raw --profile=Win7SP1x64 dumpfiles -Q 0x000000003fac3bc0 -D important
# Find password of rar file by uppercase of hash of Alissa's password
volatility2 -f MemoryDump_Lab1.raw --profile=Win7SP1x64 hashdump
# Unrar file
unar important.rar (Password required!)
```
###### flag3.png will be dropped
![App Screenshot](images/lab1_flag3.png)

## Contributing

Pull requests are welcome. For major changes, please open an issue first
to discuss what you would like to change.

Please make sure to update tests as appropriate.

## License

[MIT](https://choosealicense.com/licenses/mit/)
