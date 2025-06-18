# 🧠 Unicorn Py Test

This project contains Python scripts for **real-time data acquisition, visualization, and analysis** of EEG signals using the **Unicorn Hybrid Black** device through the **LINUX C API wrapper**.

## 📁 Project Structure

```
Unicorn_py_test/
├── unicorn_c_api_wrapper.py                # Python wrapper for Unicorn C API using ctypes
├── unicorn_receive.py                      # Minimal script to print raw EEG data to console and CSV
├── unicorn_live_view.py                    # Live plotting of EEG signals (matplotlib)
├── unicorn_live_band_power.py              # Computes and plots band power (Delta, Theta, Alpha, etc.) live
├── unicorn_live_band_power_filter_attempts.py # Experimental filters for live power estimation
├── unicorn_live_frequencies.py             # Computes FFT on live EEG data
├── lib/libunicorn.so                       # Required Unicorn shared library
├── data/                                   # Output CSVs with recorded or processed EEG data
└── __pycache__/                            # Python cache directory
```

---

## 🚀 How to Use

> You must be on a LINUX OS, it was originally developed in Ubuntu 22.04
> Make sure you have the Unicorn device drivers and `libunicorn.so` set up.

### 1. Install Requirements

```bash
pip install numpy matplotlib scipy
```

### 2. Run Examples

- **Raw Data Streaming:**

```bash
python3 unicorn_receive.py
```

- **Live EEG Visualization:**

```bash
python3 unicorn_live_view.py
```

- **Live Band Power (Alpha, Beta, etc.):**

```bash
python3 unicorn_live_band_power.py
```

- **Live Frequency Spectrum (FFT):**

```bash
python3 unicorn_live_frequencies.py
```

---

## 📄 Code Overview

| File | Description |
|------|-------------|
| `unicorn_c_api_wrapper.py` | Loads `libunicorn.so` and exposes C functions via `ctypes`. Manages buffer allocation and API calls. |
| `unicorn_receive.py` | Connects to the device and logs raw EEG data to the console and `data/unicorn_data_py.csv`. |
| `unicorn_live_view.py` | Streams data and displays real-time EEG waveform using Matplotlib. |
| `unicorn_live_band_power.py` | Computes band power values (Delta to Gamma) and plots them in real time. |
| `unicorn_live_frequencies.py` | Applies FFT on live EEG signals and shows spectral content. |
| `unicorn_live_band_power_filter_attempts.py` | Variant of the above, testing different filter implementations. |
| `lib/libunicorn.so` | Unicorn API dynamic library – required at runtime. |
| `data/*.csv` | Recorded EEG sessions, logs from live acquisition and analysis. |

---

## 📌 Notes

- Set `LD_LIBRARY_PATH=./lib` if the wrapper fails to find `libunicorn.so`.
- Ensure only **one** Unicorn session is active at a time.
- Data is sampled at 250 Hz by default.

---

## 🧠 EEG Bands Reference

| Band | Range (Hz) | Function |
|------|------------|----------|
| Delta | 0.5–4 | Deep sleep |
| Theta | 4–8 | Drowsiness, meditation |
| Alpha | 8–13 | Calm wakefulness |
| Beta | 13–30 | Alertness, concentration |
| Gamma | >30 | Cognitive tasks |

---

## 📬 Contact

Created by Rogelio Ruiz based on the official [Unicorn Hybrid Black Linux C API](https://github.com/unicorn-bi/Unicorn-Suite-Hybrid-Black/tree/master/Unicorn%20Linux%20C%20API/x64)
