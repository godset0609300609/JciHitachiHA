# Jci-Hitachi Home Assistant Integration

## Feature
A home assistant integration for controlling Jci Hitachi devices, using [LibJciHitachi](https://github.com/qqaatw/LibJciHitachi) backend.

## Installation

### Configuring via UI

1. Create `config/custom_components` folder if not existing.
2. Copy `jcihitachi_tw` into `custom_components` folder.
3. Click `Configuration` button on the left side of Home Assistant panel, and then click `Integrations` tab.
4. Click `ADD INTEGRATION` button at the bottom right corner and follow the UI.

### Configuring via `configuration.yaml`

1. Create `config/custom_components` folder if not existing.
2. Copy `jcihitachi_tw` into `custom_components` folder.
3. Configure your email address, password, and device names, in `config/configuration.yaml`. If device names are not provided, they will be fetched from the API automatically. (not recommended.)
4. Restart Home Assistant.

*An example of `configuration.yaml` can be found [here](configuration.yaml).*

## Supported devices

*支援以下使用日立雲端模組(雲端智慧控)的機種與功能*

- Hitachi Air Conditioner 日立冷氣
  - Power 電源
  - Mode 運轉模式
  - Air speed 風速
  - Vertical wind swingable 導風板垂直擺動
  - Vertical wind direction 導風板垂直方向
  - Horizontal wind direction 導風板水平方向
  - Target temperature 目標溫度
  - Indoor temperature 室內溫度
  - Mold prevention 機體防霉
  - Energy saving 節電
  - Fast operation 快速運轉
  - Power consumption 用電統計 (supports HA core v2021.9.0+)
  - Monthly power consumption 月用電統計
  - ~~Sleep timer 睡眠計時器~~ (Only supported by LibJciHitachi)
  - ~~Freeze clean 凍結洗淨~~ (Only supported by LibJciHitachi)
- Hitachi Dehumidifier 日立除濕機
  - Power 電源
  - Mode 運轉模式
  - Air speed 風速
  - Wind swingable 導風板擺動
  - Target humidity 目標濕度
  - Indoor humidity 室內溼度
  - Water full warning 滿水警示
  - Error warning 錯誤警示
  - Clean filter notify 濾網清潔通知
  - Mold prevention 機體防霉
  - PM2.5 value PM2.5數值
  - Odor level 異味等級
  - Air cleaning filter setting 空氣清淨濾網設定
  - Power consumption 用電統計 (supports HA core v2021.9.0+)
  - Monthly power consumption 月用電統計
  - ~~Sound control 聲音控制~~ (Only supported by LibJciHitachi)
  - ~~Display brightness 顯示器亮度~~ (Only supported by LibJciHitachi)
  - ~~Side vent 側吹~~ (Only supported by LibJciHitachi)
- ~~Hitachi HeatExchanger 日立全熱交換機~~ (Under development)

## Tested devices

*Below models have been tested on my side or reported by someone whose device works normally. Unlisted models DO NOT MEAN they are not supported.*

### Air conditioner

- Window
  - RA-36NV1
  - RA-28NV1
- Single-split and multi-split
  - RAD-90NJF / RAC-90NK1
  - RAS-81NK
  - RAC-63NK
  - RAS-50NJF / RAC-50NK
  - RAS-40NK
  - RAS-36NJF / RAC-36NK
  - RAS-36NK  / RAC-36NK1
  - RAS-28NJF / RAC-28NK
  - RAS-28NB / RAC-28NB
- Business
  - RPI-90FK
  - RPI-36FR
  - RPI-28FT
  - RPI-22FC

### Dehumidifier

- RD-360HH
- RD-240HH
- RD-200HH
- RDI-640HH
- RDI-360DX

## Frequently asked questions

1. I cannot install the integration, the log indicates `Requirements for jcihitachi_tw not found: ['LibJciHitachi==x.x.x']`, where x is an arbitrary version number.
    - Ensure your the OS in which your Home Assistant is installed is of the following types: `Windows`, `macOS`, `manylinux`, and `musllinux`. Only 64 bit OSes are supported on ARM platforms, e.g. Raspberry PI. Other platforms such as PowerPC and MIPS are not supported.
2. When auto mode is set, the target temperature indicates `65535` or some huge number.
    - It is normal. Technically, because the target temperature changes automatically under auto mode, the value is set 2-complement `-1` in 16 bit data type by Hitachi cloud.

## Known issues

1. Clean filter notification of the dehumidifier doesn't work now.

## License

Apache License 2.0
