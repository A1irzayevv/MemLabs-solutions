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
volatility -f MemoryDump_Lab1.raw imageinfo
volatility -f MemoryDump_Lab1.raw --profile=Win7SP1x86 pslist
volatility -f MemoryDump_Lab1.raw --profile=Win7SP1x86 cmdscan
volatility -f MemoryDump_Lab1.raw --profile=Win7SP1x86 consoles
```
Flag encoded: ZmxhZ3t0aDFzXzFzX3RoM18xc3Rfc3Q0ZzMhIX0=

Flag: flag{th1s_1s_th3_1st_st4g3!!}

## Contributing

Pull requests are welcome. For major changes, please open an issue first
to discuss what you would like to change.

Please make sure to update tests as appropriate.

## License

[MIT](https://choosealicense.com/licenses/mit/)
