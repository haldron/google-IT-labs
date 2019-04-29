
1. Verify same error on production and test server.
2. Ensure the filename in the url is correctly named in the directory, if not, rename it with mv or provide the file.
```
# sudo mv about_us.html aboutus.html
```
3. Check permissions and directory file details.
```
# ls -lah
```
4. If file is not accessible by server -give read permission for others to read the test.html file.
```
# sudo chmod o+r test.html
```
