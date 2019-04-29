## Lab - Hands on with hashing
Generate md5 sum
```
# md5sum file.txt > file.txt.md5
```
Verify md5sum with original file
```
# md5sum -c file.txt.md5
```
Generate SHA1 sum 
```
# shasum file.txt > file.txt.sha1
```
Verify SHA1 sum with original file
```
# shasum -c file.txt.sha1
```
Generate SHA256 sum
```
# shasum -a 256 file.txt > file.txt.sha256
```
Verify SHA256 sum 
```
# shasum -c file.txt.sha256
```
