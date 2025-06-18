Linux C API obtained from the official Unicorn repository: [link](https://github.com/unicorn-bi/Unicorn-Suite-Hybrid-Black/tree/master/Unicorn%20Linux%20C%20API/x64)

## 📄 File Descriptions

| File / Folder                  | Description |
|-------------------------------|-------------|
| `src/dataAcquisition.cpp`     | Main C++ example that connects to the Unicorn EEG device, starts data acquisition, saves the stream to `data.csv` and `data.bin`, then stops acquisition after a fixed duration. Uses the Unicorn C API. |
| `include/unicorn.h`           | Header file provided by g.tec, contains declarations for all Unicorn API functions and constants. Required for compilation. |
| `lib/libunicorn.so`           | Shared object library that implements the Unicorn API. Needed at both compile time (`-lunicorn`) and runtime (`LD_LIBRARY_PATH`). |
| `dataAcquisition`             | Compiled binary produced from `dataAcquisition.cpp`. Run this to start logging EEG data. |
| `data.csv`                    | Output file in CSV format containing the recorded EEG and IMU data. |
| `data.bin`                    | Output file in binary format with the same data as `data.csv`, useful for fast parsing or archival. |
| `UnicornLinuxCAPI.pdf`        | Official PDF documentation from g.tec explaining the full Unicorn Linux C API in detail. |


## How to Use

From the Linux_C_API_TETS folder

### Compile the example  

`g++ -Iinclude -Llib src/dataAcquisition.cpp -lunicorn -o dataAcquisition`

### Execute the Example
`LD_LIBRARY_PATH=./lib ./dataAcquisition`
