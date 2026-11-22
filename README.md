# PassGuard

**A simple command-line password strength checker that also tells you if your password has appeared in a known data breach.**

पासवर्ड की मज़बूती जाँचने वाला एक आसान टूल, जो यह भी बताता है कि आपका पासवर्ड कभी डेटा लीक में आया है या नहीं।

---

## Features

- Strength score from 0 to 100 with a clear rating
- Checks length, upper/lower case letters, digits and symbols
- Detects common weak patterns (`password`, `123456`, `abcd`, repeated characters)
- Breach check using the [Have I Been Pwned](https://haveibeenpwned.com/Passwords) API
- Privacy-friendly: your full password is **never** sent anywhere. Only the first 5 characters of its SHA-1 hash are sent (k-anonymity)
- Password is hidden while typing
- Output in Hindi (Devanagari)
- No external dependencies, standard library only

## Requirements

- Python 3.8 or newer
- Internet connection (only for the breach check)

## Installation

### 1. Clone the repository

```bash
git clone https://github.com/sanjaysingh-lang/PassGuard.git
cd PassGuard
```

Or just download `password_checker.py` and put it in any folder.

### 2. (Optional) Create a virtual environment

**Linux / macOS**

```bash
python3 -m venv venv
source venv/bin/activate
```

**Windows (PowerShell)**

```powershell
python -m venv venv
venv\Scripts\Activate.ps1
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

This project uses only the Python standard library, so nothing extra will be installed.

## Usage

```bash
python password_checker.py
```

On Linux/macOS you may need `python3` instead of `python`.

Type your password when asked (it will not appear on screen). The tool then shows:

1. Score out of 100
2. Rating (कमज़ोर / ठीक-ठाक / मज़बूत / बहुत मज़बूत)
3. Breach check result
4. Suggestions to improve the password

## How the breach check works

1. Your password is hashed locally with SHA-1.
2. Only the first 5 characters of the hash are sent to the HIBP API.
3. The API returns all hash endings that match those 5 characters.
4. The tool compares the rest of your hash locally.

So the API never learns your password or its full hash.

## Tips for a strong password

- Use 12 or more characters
- Mix upper case, lower case, digits and symbols
- Avoid names, birthdays and common words
- Use a different password for every account
- Use a password manager

## Project structure

```
passguard/
├── password_checker.py
├── requirements.txt
├── README.md
└── LICENSE
```

## Disclaimer

This tool is for education and personal use. A high score does not guarantee safety. Never share your passwords with anyone.

## Contributing

Pull requests are welcome. For big changes, please open an issue first to discuss what you would like to change.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
