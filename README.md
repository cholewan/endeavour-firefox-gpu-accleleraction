# endeavour-firefox-gpu-accleleraction
This guide is only for nvidia cards.

## 1. Install VA-API
`pacman -S libva-nvidia-driver`

## 2. Install libva-utils
`pacman -S libva-utils`

## 3. Verifying VA-API
Run `vainfo`
```
$ vainfo
Trying display: wayland
vainfo: VA-API version: 1.22 (libva 2.22.0)
vainfo: Driver version: VA-API NVDEC driver [direct backend]
vainfo: Supported profile and entrypoints
      VAProfileMPEG2Simple            : VAEntrypointVLD
      VAProfileMPEG2Main              : VAEntrypointVLD
      VAProfileVC1Simple              : VAEntrypointVLD
      VAProfileVC1Main                : VAEntrypointVLD
      VAProfileVC1Advanced            : VAEntrypointVLD
      VAProfileH264Main               : VAEntrypointVLD
      VAProfileH264High               : VAEntrypointVLD
      VAProfileH264ConstrainedBaseline: VAEntrypointVLD
      VAProfileHEVCMain               : VAEntrypointVLD
      VAProfileVP9Profile0            : VAEntrypointVLD
      VAProfileHEVCMain10             : VAEntrypointVLD
      VAProfileHEVCMain12             : VAEntrypointVLD
```

## 4. In firefox set optnions in `about:config` page:
| Option | Value |
| --- | --- |
| gfx.webrender.all | true |
| media.ffmpeg.vaapi.enabled | true |
| media.hardware-video-decoding.force-enabled | true |
| media.rdd-ffmpeg.enabled | true |

## 5. Add environment variables 
`nano /etc/environment`
```
MOZ_DISABLE_RDD_SANDBOX=1
LIBVA_DRIVER_NAME=nvidia
```

## 6. Veryfication
In page `about:support` you can veryfi by looking for hardware decoding 

## 7. Install extenction for better expirience
`https://addons.mozilla.org/en-US/firefox/addon/enhanced-h264ify/`
In addon block codecs that are unsupported by your browser.


