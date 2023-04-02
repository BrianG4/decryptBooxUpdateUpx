# decrypt Boox Update Upx

Have been tested only in [these Boox ereaders](#the-strings). If you found it available for any other Boox ereader, please [submit the strings](CONTRIBUTING.md#new-strings).

Note 1: There is also [another method to fetch decrypted `update.zip`](https://github.com/Hagb/decryptBooxUpdateUpx/issues/1) from [@shunf4](https://github.com/shunf4).

Note 2: There is [a way to get downloading url of latest firmware](https://github.com/Hagb/decryptBooxUpdateUpx/issues/2#issuecomment-704006389).

Note 3: `payload.bin` can be extracted with <https://github.com/cyxx/extract_android_ota_payload>.

Any other issue and pull request is also welcomed!

[The detail of algorithm (Simplified Chinese)](algorithm-zh_cn.md)

## How to run?

Python3 should be installed to run the script, and `pycryptodome` a dependency of the script should also be installed:

(BTW: in some environments, the following `pip` and `python` should be replaced with `pip3` and `python3`)

```bash
pip install pycryptodome
```

You can run the application by putting `update.upx` file in the project directory and running

```bash
python DeBooxUpx.py <device model> [input file name [output file name]]
```

`<device model>` is required, and `[input file name [output file name]]` is optional. The input file will be `update.upx` and the output file will be saved in the current working directory, if not set in the arguments.

For list of currently supported models please refer to the [table](#the-strings).

## API

There is a python class `DeBooxUpx` in [DeBooxUpx.py](DeBooxUpx.py) to decrypt `update.upx`, and dict `boox_strings` where there are known strings.

Following is a example to use this class to decrypt the `update.upx` of Boox Nove Pro:

``` python3
from DeBooxUpx import DeBooxUpx, boox_strings
model = 'NovaPro'
updateUpxPath = 'update.upx'
decryptedPath = 'update.zip'

decrypter = DeBooxUpx(**boox_strings[model])
print('When updating, the device decrypt update package into', decrypter.path)
decrypter.deUpx(updateUpxPath, decryptedPath)
```

Or for manually setting strings:

``` python3
from DeBooxUpx import DeBooxUpx

MODEL = "NovaPro" 
STRING_SETTINGS = "j857wYAQcWZgvIEQ/tcQqzxreUJgFHwJl6D2TN9BuSkQ" 
STRING_UPGRADE = "+soGw/YVdGIRJiAs5SMmv1ihW37H1Fa9+/1w2Vgt14Ag" 
STRING_LOCAL = "lpsj9NJ8Kzv8jHb+OO8A5lxC+9Zhl243bFmDZYaF" 
updateUpxPath = 'update.upx'
decryptedPath = 'update.zip'

decrypter = DeBooxUpx(MODEL, STRING_SETTINGS, STRING_UPGRADE, STRING_LOCAL)
print('When updating, the device decrypt update package into', decrypter.path)
decrypter.deUpx(updateUpxPath, decryptedPath)
```

## The strings

<!-- DO NOT MANUALLY MODIFY THE FOLLOWING TABLE -->
<!-- It is automatically generated by update_readme_strings.py -->
<!-- To update it, just update DeBooxUpx.py and run update_readme_strings.py -->
<!--(strings table begin)-->
|          |   MODEL    |               STRING_SETTINGS                |                STRING_UPGRADE                |               STRING_LOCAL               |
|----------|------------|----------------------------------------------|----------------------------------------------|------------------------------------------|
|Gulliver-ru|`MC_GULLIVER`|`wDNy4yMayA4nnQfzAYYqV3ih6uu363MoyfhaX9MtbCQk`|`xzUDklMaz39aPNJAl45ca7c3hOrBQlNYZh+iZdK64fIo`|`3xRR0nR2lFLKpw5g71X5JGqc0/hZQhmJM9idyx1b`|
|KonTiki2-ru|`Kon_Tiki2` |`eqxOVE1h8e8hbGNiV2ZHed6hMpcOH3vULx6XMm/WguZ1`|`dKA6Ik0R95nDwjGR/dfPwxkYYNBkfngJk51A2MlRxBsq`|`bPBuYxkL37AYgKbD6nRxEL6EaFCFzFgPij53pTwH`|
|   Leaf   |   `Leaf`   |`kh5V130fLNcO5lgsSDq7aUxQOz98DzEmiur3YsYKreIs`|`kBtW135kW9zvvgRlsTolCktkJ7+MeW5ZoNgr3xyr2SpX`|`jzx1lloJdIBGjmcyS9oYPmXvTKFp4dpj66fPcaON`|
|   Max2   |   `Max2`   |`vtIkV3LyRAzlnqbIHX3PFsRUI4iP6AgBDlYmkw8OtkZQ`|`uqhRVHL0SwBFPHF8wgyzGaR9XhIlkW/1ab0p7UjuDCjo`|`pvRyElGZH1rWeTUPJ8K3uV2MqyYmjpYYTW2y1Grc`|
|   Max3   |   `Max3`   |`1wdvUHZmcz32N1pgG4fkHmDsTDVihMJsPCNV4mW/6u1k`|`3nxuLgdpBE3B3n1Yyymt4cOS8dNucfQxK8YOsmcemuyO`|`yCA9YlFxLBdLbDUl3vwzPkn9vtYuVFZCfhrOTvR1`|
| MaxLumi  | `MaxLumi`  |`mTZFN0K+oMcGnn2n7+zV5DH7kr/Hbes2x/wKDJp6K7Kq`|`mj0zR0Oy3L4R+6y49MIEQT9bdx9AVz8TWyG9q3N+d9VY`|`hWAUdhOp9ekIYxIW+LpVj6OviWBbCbRa1c7s1jtW`|
| MaxLumi2 | `MaxLumi2` |`zR5/dfK/2XhmwhA9AIGr+gx6Vzho5sbklSTjLAgnC8/C`|`zh98dPzN0QdwbRem1Yfx28DFxU+Gkvg4MpLDIp0GorRU`|`                                        `|
|   Note   |   `Note`   |`0WZeSahj4BlwNAJJkcSJEdktwbc2xdYhN+pEl+7XwuJv`|`oRJROqUQ4xgcx7zvmLyPLeysH+cCU39EGXg77NZar8AP`|`z0YIfPx+vETibLDToPlDQPl54yE55JUFayfkx1+G`|
|  Note2   |  `Note2`   |`etwiPPEXAQRj3m+e0Q2FOxT16aJ8XexQAqhGn5NqZWv1`|`et0jSPpmd3ueGHLmMf+2yyXVn18sa2HrDg56dCTFH6lf`|`YY9wfqN7K1LlSug47Tr5Y8QkDHmmJ4VDCJ58mhoV`|
|  Note3   |  `Note3`   |`uTiMM5JgTXOCZAZKMcZIzc1yQpfX1+jxTFOred3te4z9`|`zEf3SZ8TOADA8QuwOHicGLrrc4EA7sffKfc01TlUfe/q`|`pmXVBMt5EllxXhD9L6/NWH/pTZXRURP6QLsrNlx6`|
| NoteAir  | `NoteAir`  |`U04vqHYo0LFoJQAvP3Rs1aBxySs7z4T1B+asamimEoAf`|`VD1ZqgIl08305CVeftRI7qGBtq9bCMrJ3a1VkpkzjOu2`|`PW8K6VI//Zt6iqjYQWN0LIwRTVYyDHJvHNEXFwWV`|
| NoteAir2 | `NoteAir2` |`iCTAyj86sQAvF/XUuLBO2dS4AWZVJsy+pPmvR9wkKqhe`|`iCbPzTBHtXSRc3HdNnswRPX6Vp222OGR/rgGb3ZYtKIM`|`                                        `|
|NoteAir2P |`NoteAir2P` |`9dRjKa5Bv6SumZaiR6B5Bmxgu/JuRoSCdqVEX1P8itHp`|`9aBiXK02yte/JCfSq1/AtQg74phmxvZv1dGaRVsM646e`|`                                        `|
| NotePro  | `NotePro`  |`MjR72bOazBUacJwDcuWgtm/E0A9F9ahIt1buweEPA020`|`RjV8r7+fx2Wjp6rUSrBOpmqYnHKs7eReqTTcy9k4c3tn`|`W2co6eaDmEl7jIjOSqr11C71RDHHiV3p5oG2G54X`|
|  NoteS   |  `NoteS`   |`+YKimeg208RzM8InqtuUjSIopyM2OLIMpFeeTQby2Au4`|`+vap6p4w0MaT5A8RB4+ru3gnFtIq2g4K+tcjQjy3N599`|`5qT7388vj+/FwLMX/cIXSCgSxSIg9SAf0tB4NcEI`|
|  NoteX   |  `NoteX`   |`xhffOONo9wDGZquv93yJoLm0z6igW+XL17PUyfR8ky4l`|`zBGvTe9t8HZQXu2Q85Dl0iI9R9tEg2VRw/8cEYXauU3o`|`                                        `|
| Note_YDT | `Note_YDT` |`Utaad8dgPmSgBOjFknI0PQAp/Sc+v71Hml0ldJIzecDx`|`ItvgBbJhOxaKjMyiE/yDufmOWwHvTPNfxdOJ2XQTHXaO`|`PIe5RuMNYz8G5FmaqRUu2qHI0br1Is3too/sLts/`|
|   Nova   |   `Nova`   |`L0uopm+jYaWWf/0e/POLt0kkBuS3H+5axpS6cqUpn4ft`|`XE6jpB3WZ9J5xQdh6GFchFbeBMALt6Zx/UIg8jaiaI72`|`Rh/6kzjOT4nJCsXC5JMEkcbPzzBmNkB8i/c6ZNun`|
|  Nova2   |  `Nova2`   |`lxXh4Vv6aqYecCAFc/hsn4mnXNbI6H4S3bZFW5Jh8NHj`|`lBabky+FbaOtZ7luDK+7BlApiYcGEi8PndwIc5WaemXQ`|`iDDDo3jsN4hhLA3tQhaIkM4XLcxZT4czBMM7ExnK`|
|  Nova3   |  `Nova3`   |`VUkFew9KjsE54uQMSZI+S2tT1RRckT/vKkfiFFqImxi7`|`VEsMcHw88MpwOByhT7zqNhRFTQcruVMqhdllIlY6T+6f`|`TGlcNi8npJe4EHxzOKbCXakJKDssoRldHueY5OGl`|
|Nova3Color|`Nova3Color`|`5VJqMbDB52k04k29Wc4itQBtLTRDq5kEdQaQ+GZ324PC`|`ky0eR7CymhuAUrRBaeii5tq/ezcnXMQkT+WV1OrmRqQa`|`/Q89A5Xbsza/FBiIu8LUV5bIiLf9kXDjAdJPjyz+`|
| NovaAir  | `NovaAir`  |`6NTlwbVEYP1BPTdQE25u6TCpoCg988I/Cjcs0Wxrwa4O`|`66aRwLgxGv1vNmOsbVWp37OBy4RugvpZvUom3VQxWGrM`|`9YDFh+EuTqFECXRvmEbL78mtW69CQRENjADM8A+L`|
| NovaAirC | `NovaAirC` |`ycihhTCxjfQO85KdVPvpA1ZzCPr3eJ/KhcKEKlqMhEfR`|`zsnQgzXEhvsfL4pk48rtEckIPyDedhybURHP198tag+Z`|`                                        `|
| NovaPlus | `NovaPlus` |`MtoBkApRAVwzdGe2CTnaE4MIgevRYNQfaKo606tyUQNY`|`Nttwkwxaei8xorBu/uUBpUu8nNZHTRIAZMZc0xrJs9Ti`|`LIYj1F9NVXFrOfi24/C76gFFxHYSCJ4mfhYI4q5w`|
| NovaPro  | `NovaPro`  |`j857wYAQcWZgvIEQ/tcQqzxreUJgFHwJl6D2TN9BuSkQ`|`+soGw/YVdGIRJiAs5SMmv1ihW37H1Fa9+/1w2Vgt14Ag`|`lpsj9NJ8Kzv8jHb+OO8A5lxC+9Zhl243bFmDZYaF`|
|  PadMu3  | `PadMuAP3` |`TCP3lGFLuxm7wOXWnaomQAdYikpFPAOj5U2LK0Dck3Un`|`PC3wkRM4zhgstNIQLGR+dW9jourXdEXZXU/mN7bTACu0`|`In/UoUFVkUdHTCqlSfCgKi8MEZGHK0Xc70Y5trXs`|
|  Poke2   |  `Poke2`   |`Lu3Xbc5vobO/8sveD6qjO/LEYeqd199myw3pybHynUEO`|`WOqqHbls0bZ67ofyutQ+XG37zR09inkP+4G3Z/t9e7m6`|`QrzzLZp3/uz4MwBzb6SJ040+l8AshzAz1t/rG8B/`|
|Poke2Color|`Poke2Color`|`I7ewiUSud0x9auT0PKp29393K5Hg3ymr1VJY5eUhoHEm`|`JLe4ijbRcj5L8S9cRPRGL7eoEIKjT8OOblhy/wyvSbze`|`SODgyWbHLhfjy4WWk6lhqhYXnP1FTjSjtzMTyZkl`|
|  Poke3   |  `Poke3`   |`lU95mOkt0cGucrsrIdAWuYnoJEnTTfIvu/QNUlcmI42A`|`kjl4lOMqobWYQyqX4KzBGYS8Q0OwPSfqwf29ymkypULP`|`iW9b2bszjJhv3puv87HNQXLW3Fb5uQVhWnnKU4nV`|
|  Poke4   |  `Poke4`   |`uTKx3XVyRhlbI7hoHuy/NiYdwlWViPlc4EecZKYTThN/`|`vzDFqwIEMRfqTPUCV82ahjnz0hXfcZCIxRY8ljuLmTaf`|`                                        `|
|Poke4Lite |`Poke4Lite` |`9SHJReeuD4hvqiwtY8mNlKTYqGkvgao4d9/9og7/EXhV`|`hiDOQumqD/7tGPsr5l69IdujC33cOPwOQw6C9wE8s8Xn`|`                                        `|
|  Poke4S  |  `Poke4S`  |`iq8+KrwLX7JGcq/B823vpSmVn5CJR2QscYDeArKjtn0B`|`+txDKcp4Kse6Ve1kBswZWQ68i+Kpab8BoXDrgpmqQrjz`|`                                        `|
| Poke_Pro | `Poke_Pro` |`6GxQ6Iei3y2PSf6Wlayz+0f6yVnl1GXe5OC3q3i2lasO`|`72lZ7vTQoy9/ESDKRQtx2V5uBMDiR+ik3n+soo9wGAbJ`|`hkkAqdfM93RpnCgXxhUqzme3OMzT6tDWC3fyibgW`|
|SP_NoteSL | `SP_NoteS` |`XjzywnKKh3FNVKphg5MZ9xILmDNYBZiCHTnkd6Q0fqpq`|`XDeIyQKAhQKj6/UmdAIWoL0aXmw9PeEFl9OpII/1TO9i`|`QmGqhFGXqiuQ9yoeVx0a2SQ8BNojjPn96o6hQW6U`|
|   Tab8   |   `Tab8`   |`Yjr0qRHMwEvCt4U3K5QtAVT97968eeMOFF2zx6f6ctFg`|`E0+HqBG5s0Z9WT+eKt0oTL2BucEMDdsaElDGQQFOV9uF`|`                                        `|
|livingstone-ru|`LIVINGSTONE`|`ES5zbiHTesxFb+zdkjxiqJ+1dOwyOCv2BzCV7fOYDJxf`|`EFwGaFSherxX1k6Hl/U6TiQhGJOzTPDfsPzHg+z9guln`|`fQ5TLnfKUOHq0f7XXdu9b1FGAckqI576ZBPkZfPg`|
<!--(strings table end)-->

The models sold in Russia are marked with suffix `-ru`, **some or all of the firmwares for which don't use the same strings with their international versions!**

PS: SP\_NoteS is SuperStar (chaoxing) verison.

### How to get the strings (Method 1, for Android <= 10)

`MODEL` string is the model name, exactly the output of `getprop ro.product.model` and/or value of `ro.product.model` in the file `/system/build.prop`.

Other strings can be got in following steps:

1. Get `/system/app/OnyxOtaService/OnyxOtaService.apk`
    
    USB Debugging (adb) is one of the the available ways:
    
    1. Turn on adb in Settings -> Applications -> USB Debugging Mode
    2. (from [@mgrub](https://github.com/mgrub)'s [note](https://github.com/Hagb/decryptBooxUpdateUpx/issues/5)) Connect the ebook to computer by usb, run
       ``` shell
       adb wait-for-device
       adb shell 'pm list packages -f | grep ota'
       ```
       And then the path of ota package will be showed. For example, the following output is in Nova Pro:
       ```
       package:/system/app/OnyxOtaService/OnyxOtaService.apk=com.onyx.android.onyxotaservice
       ```
       So in this case the path is `/system/app/OnyxOtaService/OnyxOtaService.apk`.

       In the following steps, we assume that the path is `/system/app/OnyxOtaService/OnyxOtaService.apk`.

    3. Run the following command
       ``` shell
       adb pull /system/app/OnyxOtaService/OnyxOtaService.apk .
       ```
    Now the apk is got.

2. Get the strings from apk

    1. Use [Apktool](https://github.com/iBotPeaches/Apktool) to decode the apk:
       ``` shell
       apktool d OnyxOtaService.apk
       ```
    2. Now the strings should be in `./OnyxOtaService/res/values/strings.xml`, for example the NovaPro one:
       ``` xml
       <?xml version="1.0" encoding="utf-8"?>
       <resources>
           <string name="settings">j857wYAQcWZgvIEQ/tcQqzxreUJgFHwJl6D2TN9BuSkQ</string>
           <string name="upgrade">+soGw/YVdGIRJiAs5SMmv1ihW37H1Fa9+/1w2Vgt14Ag</string>
           <string name="local">lpsj9NJ8Kzv8jHb+OO8A5lxC+9Zhl243bFmDZYaF</string>
           
       </resources>
       ```
       
      `settings` is `STRING_SETTINGS`, `upgrade` is `STRING_UPGRADE`, and `local` is `STRING_LOCAL`

3. Add and verify (optional) the strings

    Add the strings to `boox_strings` in [DeBooxUpx.py](DeBooxUpx.py), use this script to decrypt a `update.upx` file (it can be got by [the method in #2](https://github.com/Hagb/decryptBooxUpdateUpx/issues/2#issuecomment-704006389)), and see if the `update.zip` file is a vaild zip file.

### How to get the strings (Method 2, for Android >= 11)

In Boox OS since Android 11, these strings, which have been moved to `libota_jni.so`, are empty in `strings.xml`. In this case, please install and run [GetBooxUpxKeys](https://github.com/Hagb/GetBooxUpxKeysApp/releases) in your device to get keys, or refer to [22#issuecomment-964035840](https://github.com/Hagb/decryptBooxUpdateUpx/issues/22#issuecomment-964035840).

This method requires you install an apk in your device.

### How to get the strings (Method 3, for Android >= 11)

If you don't want to install the apk in **Method 2**, you can use **Method 3**. This method uses the emulator to get the strings.

`MODEL` string is the model name, exactly the output of `getprop ro.product.model` and/or value of `ro.product.model` in the file `/system/build.prop`.

Other strings can be got in following steps:

1. Get `/system/lib/libota_jni.so` (for 32-bit device) or `/system/lib64/libota_jni.so` (for 64-bit device)

    Connect to device via `adb` as above. Then execute command:

    ```
    adb pull /system/lib/libota_jni.so
    ```

    or

    ```
    adb pull /system/lib64/libota_jni.so
    ```

2. Prepare environment

    Clone the submodule.

    ```
    git submodule init
    git submodule update
    ```

    Install python dependencies.

    ```
    pip3 install unicorn capstone
    ```

3. Execute `ota_jni.py`

    ```
    python ota_jni.py libota_jni.so
    ERROR:androidemu.internal.modules:=> Undefined external symbol:
    ERROR:androidemu.internal.modules:=> Undefined external symbol: __cxa_finalize
    ERROR:androidemu.internal.modules:=> Undefined external symbol: __register_atfork
    ERROR:androidemu.internal.modules:=> Undefined external symbol: __cxa_atexit
    ro.kernel.qemu was not found in system_properties dictionary.
    libc.debug.malloc was not found in system_properties dictionary.
    WARNING:root:File does not exist '/proc/stat'
    WARNING:androidemu.internal.modules:libcrypto.so needed by libota_jni.so do not exist in vfs ExAndroidNativeEmu/vfs
    WARNING:androidemu.internal.modules:libutils.so needed by libota_jni.so do not exist in vfs ExAndroidNativeEmu/vfs
    ----------------
    STRING_SETTINGS uTKx3XVyRhlbI7hoHuy/NiYdwlWViPlc4EecZKYTThN/
    STRING_UPGRADE vzDFqwIEMRfqTPUCV82ahjnz0hXfcZCIxRY8ljuLmTaf
    ```
    
    You can test this method with `python ota_jni.py test/libota_jni.so`, which should give the above output.


## Contributing

Refer to [CONTRIBUTING.md](CONTRIBUTING.md).
