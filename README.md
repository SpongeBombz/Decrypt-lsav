# MIUI Cloud Backup Decryptor

This Python script decrypts `.lsa` and `.lsav` backup files extracted from MIUI Cloud services. It supports decrypting individual files or entire directories and attempts to automatically detect the correct file format after decryption.

---

## Features

- Decrypts `.lsa` files (full decryption) and `.lsav` files (header decryption).
- Supports decrypting a single file or all files within a directory.
- Automatically detects file type after decryption using content inspection.
- Simple usage by pasting the path when prompted.
- Decrypted files are saved alongside the original files with the correct file extension.

---

## Requirements

Install the required Python packages:

```bash
pip install -r requirements.txt
```

`requirements.txt`:

```
pycryptodome
filetype
```

Alternatively, you can install them manually:

```bash
pip install pycryptodome filetype
```

---

## Usage

1. Run the script:

    ```bash
    python decrypt.py
    ```

2. When prompted, paste the path to the `.lsa`/`.lsav` file or the folder containing them.

    Example:

    ```
    Paste the file or directory path here: C:\Users\Username\Documents\miui-backups\
    ```

3. The script will decrypt the files and save the outputs in the same directory with the appropriate file extensions.

---

## How It Works

- `.lsa` files are decrypted completely using AES in CTR mode.
- `.lsav` files have only their header decrypted using AES in CTR mode, while the remainder of the file remains unchanged.
- The AES key and initialization vector (IV) are hardcoded within the script.
- After decryption, the `filetype` library attempts to detect the file type to assign the correct extension.
- If the file type cannot be detected, the output file will use the `.unknown` extension.

---

## Important Notes

- Only files with `.lsa` or `.lsav` extensions are processed. Other files are ignored.
- The script requires Python 3.8 or newer.
- Ensure the `Crypto` and `filetype` libraries are installed before running the script.
- The original files are not modified; decrypted versions are saved separately.

---

## Example

Input file:

```
0123456789.lsa
```

Output file:

```
0123456789.jpg
```

(assuming the file content was identified as a JPEG image)

If processing a directory, all valid files inside will be decrypted.

---

## Ethical Usage

This tool is intended for educational purposes and personal data recovery only.  
Users are strictly advised to use this script ethically and **only** on data they own or have permission to decrypt.  
The author does not take any responsibility for misuse or illegal activities performed using this tool.

---

# End of Documentation
