# Magisk Delta

This repo hosts Magisk delta related files

![Delta](https://user-images.githubusercontent.com/84650617/222942594-63336f63-6a26-492e-a1d1-a356b5f777b3.png)

<img src="https://user-images.githubusercontent.com/84650617/224252197-cc54e66d-e4dd-49d4-ab8b-4506a6a3aecd.png" width="25%"/><img src="https://user-images.githubusercontent.com/84650617/223767996-f757e070-1c66-4cea-a783-e65c10640dd9.png" width="25%"/><img src="https://user-images.githubusercontent.com/84650617/224252519-2d676a3e-408d-43db-9f59-17d942d3ed9f.png" width="25%"/><img src="https://user-images.githubusercontent.com/84650617/224252589-98baf8f9-c4a1-4195-bacf-ed63908154f0.png" width="25%"/>

## Introduction

**This is not an officially supported [topjohnwu](https://github.com/topjohnwu) project**. 

> If you are looking for official Magisk source, you are in the wrong place, please [go to this page and download Official Magisk](https://github.com/topjohnwu/Magisk)

- [Internal Documents](./docs/internal-guide.md)
- [Frequently asked questions (FAQ)](./docs/faq.md)

## Download

### Stable / Beta

- [Download Magisk 25206](https://cdn.jsdelivr.net/gh/huskydg/magisk-files@301b1865c7d47bbed1e375541987aee0cd1b753d/app-release.apk)

### Canary / Debug

> ⚠ Only accept bugreports from Magisk Delta debug variant. Canary and Debug are built from the same source code. Debug builds have more detailed logs and are suitable for debugging. Canary builds have less logs, are more stable than Debug, and are suitable for most common uses

#### Download

- [Download Canary](https://huskydg.github.io/magisk-files/app-release.apk)
- [Download Debug](https://huskydg.github.io/magisk-files/app-debug.apk) 
- [Changelog](https://github.com/HuskyDG/magisk-files/blob/main/note.md)

#### Source code

- Magisk Delta is [open source under GNU v3](#license). The `source-code.zip` will be published along with released build here: <https://github.com/HuskyDG/magisk-files/releases>
- The process to build Magisk Delta is same as [Official Magisk](https://github.com/topjohnwu/magisk#building-and-development). Remember to add `-delta` prefix into `versionName` in `config.prop`.

## Donate me

- Paypal: [paypal.me/huskydg](http://paypal.me/huskydg)
- You can now donate me if you want. Remember, I will not make this as a monetization tool and donate is not obligated. Thanks for all your supports and hope you have a good day! 👍

## Other links

- [Telegram group](https://t.me/magiskdelta)

## Credits

- Magisk author: [topjohnwu](https://github.com/topjohnwu/magisk)
- Magisk contributors: [vvb2060](https://github.com/vvb2060), [yujincheng08](https://github.com/yujincheng08), [RikkaW](https://github.com/RikkaW), [canyie](https://github.com/canyie)
- SuList idea: [MagiskLite](http://t.me/magisklite)
- Maru (zygisk native bridge): [5ec1cff](https://github.com/5ec1cff)
- Other: [osm0sis](https://github.com/osm0sis), [diareuse](https://github.com/diareuse),...
- Monet design: [HardcodedCat](https://github.com/HardcodedCat), [datnerdguy](https://github.com/datnerdguy)

## License

Our license obviously is the same as [Magisk's license](https://github.com/topjohnwu/Magisk#License)

```
Magisk, including all git submodules are free software:
you can redistribute it and/or modify it under the terms of the
GNU General Public License as published by the Free Software Foundation,
either version 3 of the License, or (at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program.  If not, see <http://www.gnu.org/licenses/>.
```
