# Datasheets

Vendor documents for the parts used on ViRa_V1.0. These are the manufacturers'
own PDFs — download them from source rather than committing copies taken from
another project's repository.

| Part | Ref | Where |
|---|---|---|
| ESP32-S3-WROOM-1 | U3 | espressif.com — `esp32-s3-wroom-1_wroom-1u_datasheet_en.pdf` |
| HLK-5M05 (230 Vac → 5 V, 5 W) | U1 | hlktech.net |
| AMS1117-3.3 | U2 | Advanced Monolithic Systems |
| DS3231M RTC | U5 | analog.com |
| SRD-05VDC-SL-C relay | K2 | Songle — check coil resistance and contact rating |
| MLT-8530 buzzer | LS1 | see `../External_Libraries/ul_MLT-8530/` |
| CH291-1220LF cell holder | BT1 | see `../External_Libraries/CH291-1220LF/` |
| AO3400A N-MOSFET | Q1, Q2 | Alpha & Omega |
| USBLC6-2P6 ESD | U4 | st.com |

The two that matter most for this board: the **SRD-05VDC coil current** (sets the
AO3400A gate drive and the 5 V budget) and the **HLK-5M05 output rating** (1 A,
which is what the +5V copper is sized against).
