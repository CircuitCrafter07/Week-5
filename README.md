# 🧩 OpenROAD Flow Installation Guide (Ubuntu)

This guide provides a simple step-by-step process to install **OpenROAD Flow** on your Ubuntu system and run the test design `nand45`.

---

## 🖥️ Supported Versions

- Ubuntu **20.04** or **22.04 LTS**
- Internet connection required
- Recommended: 16 GB RAM, 4+ CPU cores

---

## ⚙️ Step 1: Install Required Dependencies

Update your package list and install the necessary tools:

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install -y git build-essential python3 python3-pip cmake clang bison flex libreadline-dev gawk tcl-dev libffi-dev graphviz xdot pkg-config libboost-system-dev libboost-python-dev libboost-filesystem-dev zlib1g-dev
```

---

## 📦 Step 2: Clone the OpenROAD Repository

```bash
git clone https://github.com/The-OpenROAD-Project/OpenROAD.git
cd OpenROAD
```

---

## 🔧 Step 3: Install Dependencies

Run the dependency installer script:

```bash
sudo ./etc/DependencyInstaller.sh -all
```

If you see an error like:

```
sudo: ./etc/DependencyInstaller.sh: command not found
```
make it executable:

```bash
chmod +x ./etc/DependencyInstaller.sh
sudo ./etc/DependencyInstaller.sh -all
```

If prompted with:
```
ERROR] You must use one of: -all, -base, or -common.
```
use:
```bash
sudo ./etc/DependencyInstaller.sh -all
```

---

## 🏗️ Step 4: Build OpenROAD

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

Run the default example flow to verify installation:

```bash
cd flow
make DESIGN=nand45
```

After completion, check the results:

```
flow/results/nand45/
```

---

## 🧹 Step 6: Clean Build Files

```bash
make clean_all
```

---

## ⚠️ Troubleshooting

| Issue | Cause | Solution |
|-------|--------|-----------|
| `command not found` | Script not executable | `chmod +x ./etc/DependencyInstaller.sh` |
| `ERROR] You must use one of: -all, -base, or -common` | Wrong argument | Use `-all` |
| `Permission denied` | Missing sudo rights | Run with `sudo` |
| Build fails | Missing dependencies | Rerun dependency installer |

---

## 📚 References

- [OpenROAD GitHub Repository](https://github.com/The-OpenROAD-Project/OpenROAD)
- [OpenROAD Documentation](https://openroad.readthedocs.io/en/latest/)

---

### ✅ Done! You have successfully installed OpenROAD Flow on Ubuntu.
