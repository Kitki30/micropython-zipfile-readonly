# micropython-zipfile-readonly

> [!TIP]
> This is a readonly fork of zipfile port for micropython by jonnor, please see original author

Support for [.zip files](https://en.wikipedia.org/wiki/ZIP_(file_format)) for [MicroPython](https://micropython.org/).
Port of CPython [zipfile](https://docs.python.org/3/library/zipfile.html).

## Installing

This package can be installed using [mip](https://docs.micropython.org/en/latest/reference/packages.html#installing-packages-with-mip).

For example:

```bash
mpremote mip install github:Kitki30/micropython-zipfile-readonly
```

Or just copy the `zipfile.py` file to your MicroPython device.

## Usage

#### List what is inside a ZIP archive
```python
# List the information from a .zip archive
print('\nListing information')
with ZipFile(path, 'r') as archive: 
    for info in archive.infolist(): 
        print(info.filename)
        print('\tSystem:\t\t' + str(info.create_system) + '(0 = Windows, 3 = Unix)') 
        print('\tZIP version:\t' + str(info.create_version)) 
        print('\tCompressed:\t' + str(info.compress_size) + ' bytes') 
        print('\tUncompressed:\t' + str(info.file_size) + ' bytes') 
```

#### Read data from a file inside ZIP archive

```python
# Read a file from inside .zip archive
print('\nReading file')
with ZipFile(path) as myzip:
    with myzip.open('test.txt') as myfile:
        print(myfile.read())
```
