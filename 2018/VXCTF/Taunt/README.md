# VXCTF 2018 : Taunt

**category** : crypto

**points** : 500

**solves** : 1

## write-up

他的明文是重複五次的 flag (ex : `CTF{FLAG}CTF{FLAG}CTF{FLAG}CTF{FLAG}CTF{FLAG}`)

那 `f(x) = ((2^(4*8*L) + (2^(3*8*L) + (2^(2*8*L) + (2^(1*8*L) + (2^(0*8*L)) * x) ^ 3 - c`

原始碼有寫長度 < 60

那就暴搜所有長度，用 coppersmith method 求 small roots 就好了

然後賽後我發現根本不用 coppersmith method

就直接

```
magic = 2 ** (8 * L * 4) + 2 ** (8 * L * 3) + 2 ** (8 * L * 2) + 2 ** (8 * L * 1) + 1
m, s = gmpy2.iroot(inverse(magic ** 3, n) * c % n, 3)
```

把 magic 的三次方 inverse 乘回去就只剩 short message

然後直接開三方就好 O_O

# other write-ups and resources

