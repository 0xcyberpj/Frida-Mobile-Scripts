# 0x01 查看运行app包，下载到本地

```
unzip -l base.apk|grep client |grep assets|grep p12
     2525  11-23-2020 13:58   assets/client.p12
     
unzip -l base.apk|grep client |grep assets|grep cer
     1306  11-23-2020 13:58   assets/client.cer
     
```

#### 从apk只解压2个证书到本地

```
unzip base.apk "assets/client.p12*" -d demo
Archive:  base.apk
  inflating: demo/assets/client.p12
  
  
unzip base.apk "assets/client.cer*" -d demo
Archive:  base.apk
  inflating: demo/assets/client.cer
```

```
tree demo
demo
└── assets
    ├── client.cer
    └── client.p12
```

```
file demo/assets/client.cer
demo/assets/client.cer: PEM certificate

file demo/assets/client.p12
demo/assets/client.p12: data
```

use **tracer_keystore.js** get keystore  password

**`frida -U -l tracer_keystore.js -f cn.xxxapp.android`**

#### **`}%2R+\OSsjpP!w%X`**
```
     ____
    / _  |   Frida 14.1.3 - A world-class dynamic instrumentation toolkit
   | (_| |
    > _  |   Commands:
   /_/ |_|       help      -> Displays the help system
   . . . .       object?   -> Display information about 'object'
   . . . .       exit/quit -> Exit
   . . . .
   . . . .   More info at https://www.frida.re/docs/home/
Spawning `cn.xxxapp.android`...
KeyStore hooks loaded!
Spawned `cn.xxxapp.android`. Use %resume to let the main thread start executing!
[Pixel 2::cn.xxxapp.android]-> %resume
[Pixel 2::cn.xxxapp.android]-> [Keystore.getInstance()]: type: PKCS12
[Keystore.load(InputStream, char[])]: keystoreType: PKCS12, password: '}%2R+\OSsjpP!w%X', inputSteam: android.content.res.AssetManager$AssetInputStream@af4064b
[Keystore.getInstance()]: type: BKS
[Keystore.load(LoadStoreParameter)]: keystoreType: BKS, param: null
[Keystore.getEntry()]: alias: a9f6f85c72b2504a172054fd64ccc2029370f81b, protection: 'Unknown protection parameter type: java.security.KeyStore$PasswordProtection'
[getEntry()]: Entry: java.security.KeyStore$PrivateKeyEntry [implement key dumping if needed] com.android.org.bouncycastle.jcajce.provider.asymmetric.rsa.BCRSAPrivateCrtKey
[Keystore.getInstance()]: type: AndroidKeyStore
[Keystore.load(LoadStoreParameter)]: keystoreType: AndroidKeyStore, param: null
```

# Frida-Mobile-Scripts - Work in Progress
Collection of useful FRIDA Mobile Scripts

## Credits 
* [Runtime Mobile Security (RMS)](https://github.com/m0bilesecurity/RMS-Runtime-Mobile-Security)
* [FSecureLABS](https://github.com/FSecureLABS/)
* [Mediaservice](https://techblog.mediaservice.net/)
* [iddoeldor](https://github.com/iddoeldor)
* [dzonerzy](https://github.com/dzonerzy)
* [akabe1](https://github.com/akabe1/my-FRIDA-scripts)
* [Areizen](https://github.com/Areizen)
* [int3rf3r3nc3](https://github.com/interference-security/frida-scripts)
* [dki](https://codeshare.frida.re/@dki/ios10-ssl-bypass/)
* [ay-kay](https://codeshare.frida.re/@ay-kay/ios-dataprotection/)
* [chaitin](https://github.com/chaitin/passionfruit)
* [lich4](https://codeshare.frida.re/@lichao890427/dump-ios/)
* [fadeevab](https://codeshare.frida.re/@fadeevab/intercept-android-apk-crypto-operations/)
* [federicodotta](https://github.com/federicodotta/Brida)
* [noobpk](https://github.com/noobpk/frida-ios-hook)
