# Brother MFC-L2800DW driver for Arch Linux

PKGBUILD for installing the LPR and CUPS drivers for the Brother MFC-L2800DW monochrome laser multi-function printer on Arch Linux.

## Prerequisites

- [CUPS](https://wiki.archlinux.org/title/CUPS) installed and running
- `cups` service enabled and started:
  ```bash
  sudo systemctl enable --now cups
  ```

## Installation

### From source

```bash
git clone https://github.com/penglezos/brother-mfc-l2800dw
cd brother-mfc-l2800dw
makepkg --install
```

## Post-Installation

After installing the package:

1. Open the CUPS web interface at http://localhost:631
2. Navigate to **Administration** → **Add Printer**
3. Select your Brother MFC-L2800DW from the list
4. Choose the **Brother MFC-L2800DW CUPS driver** from the driver list
5. Complete the setup

## Driver Details

- **Version:** 4.1.2
- **Supported architectures:** i686, x86_64
- **Dependencies:** cups, lib32-glibc (x86_64 only)
- **Printer page:** [Brother Support](https://support.brother.com/g/b/producttop.aspx?c=as_ot&lang=en&prod=mfcl2800dw_eu_as)

## License

MIT. See [LICENSE](LICENSE) for more details.
