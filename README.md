# OTDR PROTOCOL CHECKER

## Description
The OTDR Protocol Checker project consists of two Python scripts designed to automate the processing of OTDR (Optical Time Domain Reflectometer) data. Each script handles different types of data: one for raw data and the other for preprocessed data. They read data from Excel files (XLSX format), extract the relevant information, calculate the actual and allowed attenuation, and identify any values exceeding these predetermined thresholds. The scripts generate reports summarizing the processed data, indicating the number of cable lengths extracted and identifying addresses with potentially problematic attenuation values.

## Project Files

### otdr_check_rd.py
This script processes raw OTDR data.

#### Functions
1. **cable_length(path)**
   - Reads the cable lengths from the OTDR Excel files and writes them along with address information to a new Excel file.
   - First, a CSV file with the above information is created. The CSV file is then converted to XLSX format, and the original CSV file is deleted.
   - The cell parameters may need to be adjusted if the length or address information is located in different cells.
   - Returns the number of processed XLSX files.

2. **attenuation(path)**
   - Reads all the attenuation values from the OTDR Excel files and writes the address information to a CSV file if at least one of the measured attenuations is higher than a threshold value.
   - The cell parameters may need to be adjusted if the attenuation values, the values for calculating the threshold values, or the address information are located in different cells.
   - Returns the number of XLSX files that contain attenuation values higher than the threshold values.

3. **print_result(addresses, invalid)**
   - Returns a formatted string with the number of addresses and the number of invalid values found.

4. **main()**
   - This is the entry point of the script.
   - The path to the directory containing XLSX files can be specified in the command line or defaults to the current working directory.
   - Calls `cable_length` and `attenuation` functions and prints the results using `print_result`.

#### Usage
- The path parameter in the main function should be set to the directory where all the OTDR Excel files are located.
- Run the script from the command line with the optional directory argument:
  ```
  python otdr_check_rd.py [optional_path_to_directory]
  ```

### otdr_check_ppd.py
This script processes preprocessed OTDR data.

#### Functions
1. **process_otdr_files(path)**
   - Processes the OTDR Excel files to extract cable lengths, attenuation values, and other relevant data.
   - Writes the extracted data to a new Excel file and highlights any values exceeding the predetermined thresholds.
   - Returns a summary of the processed data, including the number of files processed and any issues found.

#### Usage
- The path parameter should be set to the directory where all the preprocessed OTDR Excel files are located.
- Run the script from the command line with the optional directory argument:
  ```
  python otdr_check_ppd.py [optional_path_to_directory]
  ```

### requirements.txt
The `requirements.txt` files contain all required Python libraries.

To install the required libraries, run:
```
pip install -r requirements.txt
```

## Example Commands
To run the raw data processing script:
```
python otdr_check_rd.py [optional_path_to_directory]
```

To run the preprocessed data processing script:
```
python otdr_check_ppd.py [optional_path_to_directory]
```

If no path is provided, the current working directory will be used by default.
