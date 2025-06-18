# 🧠 Unicorn Windows C API Tests

This project contains example code and binaries for using the **Unicorn Hybrid Black EEG device** on **Windows** via the official **C API**.

It demonstrates how to acquire EEG data, compile applications using Visual Studio, and interface with Unicorn's shared libraries.

---

## 📁 Project Structure

```
Windows_C_API_TESTs/
├── data.csv                               # EEG output data from test run
├── dataAcquisition.exe                    # Compiled executable to acquire EEG and save to CSV
├── unicorn_test.exe                       # Another compiled test program (uses main.c)
├── Unicorn.dll                            # Required dynamic library for runtime
├── UnicornSuiteData/
│   └── UnicornRawDataRecorder_...csv      # Sample session file saved from the device
├── include/
│   ├── unicorn.h                          # Unicorn API header file
│   ├── stdafx.h, stdafx.cpp               # Precompiled header files
│   └── targetver.h                        # Windows target version header
├── lib/
│   ├── Unicorn.dll, Unicorn.lib           # Required Unicorn library binaries
│   ├── libUnicorn.dll.a, Unicorn.def      # Import and definition files for linker
├── src/
│   ├── dataAcquisition.c                  # Example that initializes the device and logs data
│   └── main.c                             # Alternative entry point used in `unicorn_test.exe`
```

---

## 🔧 How to Compile

### 💻 Visual Studio or Visual Studio Code

First attempt running this in the MSYS 64 terminal, from within the Windows_C_API folder:

```sh
gcc src/dataAcquisition.c -Iinclude -Llib -lUnicorn -o dataAcquisition.exe
```

it should create a `dataAcquisition.exe` file

---

## ▶️ How to Run

1. Make sure `Unicorn.dll` is in the same directory as the executable.
2. Run:

```sh
./dataAcquisition.exe
```

The program should connect to the Unicorn device and save EEG data to the filepath determined in the code, default: `data.csv`.

---

## 📄 Code Overview

| File | Description |
|------|-------------|
| `src/dataAcquisition.c` | Initializes device, starts acquisition, logs EEG/IMU data, and stops. |
| `src/main.c` | A simplified alternative entry point for basic testing. |
| `dataAcquisition.exe` | Executable built from `dataAcquisition.c`. |
| `unicorn_test.exe` | Executable built from `main.c`. |
| `include/unicorn.h` | Unicorn C API declarations. |
| `lib/Unicorn.lib`, `Unicorn.dll` | Required for linking and running with the Unicorn API. |
| `data.csv`, `UnicornSuiteData/*.csv` | Sample recorded EEG sessions. |

---

## 👤 Author

Created by Rogelio Ruiz based on the official [Unicorn Hybrid Black Windows C API](https://github.com/unicorn-bi/Unicorn-Hybrid-Black-Windows-APIs/blob/main/c-api/unicorn-c-api.md)