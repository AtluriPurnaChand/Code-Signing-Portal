# Setup Guide (No Docker)

## 1) Install dependencies
```bash
pip install -r requirements.txt
```

## 2) (Recommended) Install ClamAV

### Ubuntu/Debian
```bash
sudo apt update
sudo apt install clamav clamav-daemon -y
sudo systemctl stop clamav-freshclam
sudo freshclam
sudo systemctl start clamav-daemon
```

### macOS (Homebrew)
```bash
brew install clamav
freshclam
```

### Windows
Use WSL (Ubuntu) and follow Linux steps above, or install a native ClamAV build.

## 3) Run the app
```bash
python app.py
```

On startup and during scans the app will automatically use ClamAV when available.
If ClamAV is missing, it falls back to a heuristic scanner.

## 4) Test detection
Create `eicar.com` with the EICAR test string and upload it. It should be quarantined.

Quarantine location: `tmp/quarantine/` inside the project folder.
