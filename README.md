# Brother MFC-L2800DW printer Arch Linux driver

This is a `PKGBUILD` to install LPR and CUPS driver for the Brother MFC-L2800DW printer on ArchLinux.

## Installation

Clone the repository and run the following commands:

```
$ git clone https://github.com/penglezos/brother-mfc-l2800dw
$ cd brother-mfc-l2800dw
$ makepkg --install
```

Then open the CUPS admin on http://localhost:631, add a new printer and pick the Brother MFC-L2800DW CUPS driver.