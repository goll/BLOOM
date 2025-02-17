# BLOOM (Bacterial Light OptOgenetic Matrix)

BLOOM is a configurable LED matrix used for optogenetic cell stimulation in the [MI-DNA Disc project](https://www.midnadisc.eu/). It's built using off-the-shelf components that are readily available, total cost ~€60.

![](/media/BLOOM.jpg)

## Overview

Heavily inspired by [LITOS](https://github.com/pertzlab/LITOS), right around the time I started working on it, HUB75 LED matrix support was added to [WLED-MM](https://github.com/MoonModules/WLED-MM). Since WLED runs on many boards and has a [JSON API](https://mm.kno.wled.ge/interfaces/json-api/) it was easier to rapidly prototype the MVP compared to a custom PCB solution. The case model files can be found in the `hardware` directory, including sliced 3MF for BambuStudio. There is a custom HTML interface to control the two 96-well microplates with functionality to save/load/import presets, [example preset](/media/experiment_001.json).

## Hardware

* [Adafruit MatrixPortal S3](https://www.adafruit.com/product/5778) ~€25
* [Adafruit 64x64 LED matrix P3](https://www.adafruit.com/product/4732) ~€35
* 3D printed case (~215g of filament):
  * [Bambu Lab X1C](https://bambulab.com/en-us/x1)
  * [Extrudr GreenTEC Pro](https://www.extrudr.com/shop-eu/products/greentec-pro/)

Case overview:
![](/media/case_in.png)
![](/media/case_out.png)

## UI

Plates tab:
![](/media/ui_plates.png)
Presets tab:
![](/media/ui_presets.png)

## Install

```
$ git clone https://github.com/goll/BLOOM.git
$ cd BLOOM/software/WLED
$ mv platformio_override.ini.matrixportal platformio_override.ini
$ mv wled00/my_config_bloom.h wled00/my_config.h
$ npm install
$ npm run build
```

You will need VSCode and PlatformIO, for more detailed steps visit [WLED-MM compiling docs](https://mm.kno.wled.ge/advanced/compiling-wled/). Connect your MatrixPortal and upload using the `adafruit_matrixportal_esp32s3` env. By default it will try to connect to SSID `bloom` using password `bloom123`, which should be running as a hotspot on a nearby phone/tablet/laptop. After connecting you can visit `http://bloom.local/plates.htm` to control the device.

## TODO

- [ ] Add timer functionality
- [ ] Support more microplate sizes
- [ ] Individual well brightness
- [ ] Add mounting plate diffusion grids
- [ ] Add top cover to prevent light pollution
