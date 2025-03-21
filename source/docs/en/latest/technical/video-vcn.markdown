---
Type:            article
Title:           AMD VCN
Project:         HandBrake
Project_URL:     https://handbrake.fr/
Project_Version: Latest
Language:        English
Language_Code:   en
Authors:         [ Bradley Sepos <bradley@bradleysepos.com> (BradleyS), Scott (s55) ]
Copyright:       2024 HandBrake Team
License:         Creative Commons Attribution-ShareAlike 4.0 International
License_Abbr:    CC BY-SA 4.0
License_URL:     https://handbrake.fr/docs/license.html
---

AMD VCN
=======

## Supported Hardware and Configurations

- AMD Radeon RX6000 (RDNA2), RX7000 (RDNA3) and RX9000 (RDNA4) series GPU or better
- Windows 10 or later
- Limited support is available on Ubuntu 22.04 and later.

Please note, these are not hard limits. Hardware encoding via VCN *might* work on older series GPUs and older operating systems, but this is not officially supported.

## Enabling support

<!-- .system-windows -->
Support for the AMD VCN encoder is enabled in preferences on the video tab. If your system is not supported, the option will be disabled.
<!-- /.system-windows -->

<!-- .system-linux-->
On Linux, we need the official amdgpu-pro drivers.

 - Download the latest drivers from: [AMD Radeon Software for Linux version 24.20 or later](https://www.amd.com/en/support/linux-drivers) is required to use the VCN encoder. 
 - sudo dpkg -i amdgpu-install_VERSION_all.deb   (Where version is similar to: 6.3.60302-1)
 - sudo amdgpu-install -y --usecase=graphics,amf --accept-eula
 - Reboot your computer.
 
For native installs, VCN should now be available in the HandBrake GUI.
 
If your are using a flatpak build, you will have to perform some additional steps:

 - If you don't already have [Flatseal](https://flathub.org/apps/com.github.tchx84.Flatseal) installed, you will need to install it. 
 - Open FlatSeal and choose the HandBrake app.
 - In the "Other Files" section, add a folder "/opt"
 - In the "Environment - Variables" section, change LD_LIBRARY_PATH=/app/extensions/lib:/opt/amdgpu-pro/lib/x86_64-linux-gnu
   (adding :/opt/amdgpu-pro/lib/x86_64-linux-gnu) to the end.  Note, on non-ubuntu distros, this path may be differnet. I.e RHEL/SLE it may be under: /opt/amdgpu-pro/lib64

Now, if your run HandBrake, you should see the VCN options available. 


<!-- /.system-linux -->


## Presets

The following presets are available under the 'Hardware' category in the presets menu:

- H.265 VCN 2160P 4K
- H.265 VCN 1080p

These are a good starting point for configuring HandBrake to use these encoders.

## Known Limitations

- The AV1 encoder that ships with Navi 3.x products requires a resolution that is divisible by 64 in both width and height. Becareful that the output resolution after cropping follows this rule. 


## Performance

HandBrake supports the AMD VCN hardware encoder but does NOT support the hardware decoder.

The CPU will still be used for:

- Video decoding 
- All video filters
- Audio encoding 
- HandBrake's engine, A/V sync etc
- Subtitles
- Muxing

These operations all happen in parallel as the job progresses. As such, it is normal to see high (or even 100%) CPU utilisation even when using VCN.

It is also common, particularly on lower-end or older hardware, for the CPU to be a bottleneck which will cause lower than expected performance. To minimize this effect, disable any filters that you do not require.

## Advanced options

The AMD VCN hardware encoder has a limited set of advanced encoder options. Generally speaking, it is not recommended to change these parameters, as the built-in presets offer a good range of options for common uses.

If using HandBrake’s graphical interface, you can set the options in the `Advanced Options` field on the `Video` tab in the following format:

    option1=value1:option2=value2
    
If using HandBrake’s command line interface, use the `--encopts` parameter as follows:

    --encopts="option1=value1:option2=value2"


### Option value types

The following value types are supported (each option only accepts one value type):

- integer  
  A number that can be written without a fractional or decimal component.

- boolean  
  0 means off (or disabled).  
  1 means on (or enabled).
 
- string  
  An alphanumeric string of characters. See the option’s comments for acceptable values.

### Options list

| Option                | Type        | H.264 | H.265 | Detail                                                                               |
|-----------------------|-------------|:-----:|:-----:|--------------------------------------------------------------------------------------|
| usage                 | string      |   ✓   |   ✓   | Options: `transcoding`, `ultralowlatency`, `lowlatency`, `webcam`                   |
| coder                 | string      |   ✓   |       | Coder selection. Values: `auto` (default), `cabac`, `cavlc`.                         |
| preanalysis           | boolean     |   ✓   |   ✓   | Set to `1` to enable preliminary analysis, `0` to disable (default).                 |
| vbaq                  | boolean     |   ✓   |   ✓   | Set to `1` to enable Variance Based Adaptive Quantization, `0` to disable (default). |
| enforce_hrd           | boolean     |   ✓   |   ✓   | Set to `1` to enforce Hypothetical Reference Decoder, `0` to disable (default).      |
| max_au_size           | int         |   ✓   |   ✓   | Maximum Access Unit size for rate control, in bits. Default: `0` (automatic).        |
| me_half_pel           | boolean     |   ✓   |   ✓   | Set to `1` to enable half-pixel motion estimation (default), `0` to disable.         |
| me_quarter_pel        | boolean     |   ✓   |   ✓   | Set to `1` to enable quarter-pixel motion estimation (default), `0` to disable.      |
| bf_delta_qp           | int         |   ✓   |       | B-Picture Delta QP. The values scale is `-10`–`10`. Default: `4`.                    |
| bf_ref                | boolean     |   ✓   |       | Set to `1` to enable Reference B-Frames (default), `0` to disable.                   |
| bf_ref_delta_qp       | int         |   ✓   |       | Reference B-Picture Delta QP. The values scale is `-10`–`10`. Default: `4`.          |
| intra_refresh_mb      | int         |   ✓   |       | Number of Intra-Refresh Macroblocks per slot. Default: `0` (automatic).              |
| header_insertion_mode | string      |       |   ✓   | Options: `none`, `gop`, `idr`                                                        |
| gops_per_idr          | int         |       |   ✓   | GOPs per IDR 0-no IDR will be inserted                                               |

