# 🧩 OpenROAD Flow Installation Guide (Ubuntu)

The **OpenROAD Flow** is an open-source RTL-to-GDSII flow for physical design automation.  
This guide provides step-by-step instructions to install and run OpenROAD Flow on an Ubuntu system.

---

## 🖥️ Supported Platforms

- Ubuntu **20.04 / 22.04 LTS**
- 64-bit systems
- Internet connection required

---

## ⚙️ Step 1: Install Required Packages

First, update your system and install the required tools:

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install -y git build-essential python3 python3-pip     cmake clang bison flex libreadline-dev gawk tcl-dev libffi-dev     graphviz xdot pkg-config libboost-system-dev libboost-python-dev     libboost-filesystem-dev zlib1g-dev
```

---

## 📦 Step 2: Clone the OpenROAD Repository

Download the official OpenROAD repository from GitHub:

```bash
git clone https://github.com/The-OpenROAD-Project/OpenROAD.git
cd OpenROAD
```

---

## 🔧 Step 3: Install Dependencies

The repository includes a script that installs all required dependencies automatically.

```bash
sudo ./etc/DependencyInstaller.sh -all
```

If you encounter this error:
```
sudo: ./etc/DependencyInstaller.sh: command not found
```

Try the following:

```bash
cd OpenROAD
chmod +x ./etc/DependencyInstaller.sh
sudo ./etc/DependencyInstaller.sh -all
```

If you see:
```
ERROR] You must use one of: -all, -base, or -common.
```
Run with the proper option:
```bash
sudo ./etc/DependencyInstaller.sh -all
```

---

## 🏗️ Step 4: Build OpenROAD

After dependencies are installed, build OpenROAD:

```bash
mkdir build
cd build
cmake ..
make
sudo make install
```

Verify installation:

```bash
openroad -version
```

---

## 🚀 Step 5: Run Example (nand45)

To test your setup, run the `nand45` example design:

```bash
cd flow
make DESIGN=nand45
```

After successful completion, results will be available at:

```
flow/results/nand45/
```

---

## 🧹 Step 6: Clean Build Files

To remove temporary files and logs:

```bash
make clean_all
```

---

## 🧰 Troubleshooting

| Issue | Possible Cause | Solution |
|-------|----------------|-----------|
| `command not found` | Script not executable | `chmod +x ./etc/DependencyInstaller.sh` |
| `You must use one of: -all, -base, or -common` | Wrong script usage | Run with `-all` |
| `Permission denied` | Missing permissions | Use `sudo` or ensure script ownership |
| Build fails | Missing dependency | Rerun dependency installer |

---

## 📚 References

- 🔗 [OpenROAD GitHub Repository](https://github.com/The-OpenROAD-Project/OpenROAD)
- 📖 [Official Documentation](https://openroad.readthedocs.io/en/latest/)

---

## 💡 Notes

- Recommended system: **16 GB RAM**, **4+ CPU cores**
- Use a **Python virtual environment** for isolation
- Results of each design are stored in `flow/results/`

---

### ✅ Congratulations! You’ve successfully set up OpenROAD Flow on Ubuntu.
