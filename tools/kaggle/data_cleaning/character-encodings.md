# (4) Character Encodings

https://www.kaggle.com/code/alexisbcook/character-encodings

## 1. Get our environment set up
- import libraries
    - `pandas`, `numpy` for data handling
    - `charset_normalizer` to detect unknown file encodings
- set a random seed for reproducibility
- dataset will be loaded later once encoding issues are addressed

## 2. What are encodings?
- **character encodings** define how raw binary data (bytes) are mapped to readable characters.
- using the wrong encoding causes
    - **mojibake** (garbled text)
    - **Unknown characters** (�)
- **UTF-8** is the standard encoding and should be used whenever possible

### a. Text types in Python 3
- **String** (`str`): Human-readable text (UTF-8 by default)
- **Bytes** (`bytes`): Raw binary data

### b. Encoding & decoding
- **Encoding**: Convert string → bytes
- **Decoding**: Convert bytes → string
- using the wrong encoding can:
    - raise errors
    - permanently corrupts data (like, replacing characters `?`)

! Always convert text **to UTF-8 as early as possible**

## 3. Reading in files with encoding problems 
- most files are UTF-8 and load normally with `pd.read_csv()`
- if a file is **not UTF-8**, pandas raises a `UnicodeDecodeError`

### a. How to fix:
1. open the file in **binary mode**
2. use `charset_normalizer` to guess the encoding (faster than trial-and-error)
3. read the file using the detected encoding:

```
pd.read_csv(file_path, encoding="Windows-1252")
```
- the quess is not always perfect, but usually accurate
- you can improve results by analyzing more of fewer bytes

## 4. Saving your files with UTF-8 encoding
- once data is correctly loaded, save it in UTF-8 to prevent future issues
- python saves files as UTF-8 **by default**
```
df.to_csv("file_utf8.csv")
```
- keeping data in UTF-8 ensures compatibility across systems and tools

## 5. Key takeaways
- encoding issues happen when bytes are interpreted using the wrong character set
- UTF-8 is the safest and most universal choice
- detect encoding problems early, fix them once and save everything in UTF-8