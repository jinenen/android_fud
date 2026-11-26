# TJTools - Android Security & Android App Hardening & Anti-Reverse Engineering System & Android Fully Undetectable & Android Fud

## Contact Us
![Contact Us](qrcode.png)

[Click to contact us](http://47.108.138.179:8006/?session=0b54fbc324904420)

---

## 1. Overview

**TJTools** is a high-strength security hardening and anti-reverse engineering solution designed for Android applications (supporting native Java/Kotlin, UniApp, Flutter, and hybrid frameworks).
It can truly achieve Android Fully Undetectable, abbreviated as Android Fud, which means completely undetectable

The system adopts a multi-dimensional defense architecture combining **Native C++ Runtime Defense, In-Memory Dynamic Loading, Full Resource Virtualization, and Manifest Sanitization/Anti-Decompilation Traps**. It thoroughly neutralizes static decompilation, dynamic debugging, and signature scanning by antivirus (AV) engines, while delivering high stability and full-feature compatibility across Android 12 to 14 (MIUI / HyperOS, EMUI, ColorOS, OriginOS, and other custom ROMs).

---

## 2. Core Features & Technical Highlights

### 2.1 Deep Instruction Encryption & In-Memory Multi-DEX Dynamic Loading
* **Total DEX Extraction & Encryption**: All original DEX bytecode files are stripped, obfuscated, and encrypted with strong symmetric encryption into concealed assets, leaving only a minimal protection shell in the outer layer.
* **Native In-Memory Loading Engine**: The proprietary `libtjsec.so` core intercepts the cold-start sequence, decrypting and loading bytecode directly in native memory, completely avoiding any plaintext file drops on disk.
* **Universal Hidden API Exemption Bypass**: Overcomes Android 12+ / 13+ / 14's strict restrictions on Java reflection (`access denied`) by directly triggering Native-level runtime exemptions in C++, restoring unrestricted runtime reflection capabilities for dynamic component mounting.

### 2.2 AndroidManifest Sanitization & Component Cloaking (Scheme 1)
* **Complete Outer Component Stripping**: Reconstructs binary AXML to strip all business Activities, Services, BroadcastReceivers, and ContentProviders from the outer manifest. Decompilers (such as Jadx and Apktool) only observe a bare shell entry point.
* **Dynamic Component Lifecycle Proxying**: Utilizes a custom `CoreComponentFactory` and dynamic `StubInstrumentation` proxy to seamlessly intercept and mount genuine business components at runtime without compromising activity transitions or theme styles.
* **Notification & Foreground Service Guard**: Features an automatic fallback mechanism for Android 13/14 foreground services, ensuring that missing notification icons or RemoteViews are safely substituted, completely preventing SystemUI cross-process termination.

### 2.3 Full Static Asset & Resource Encryption Virtualization
* **Physical Asset Removal**: Non-essential business layouts (`res/layout/`), images (`res/drawable/`, `res/mipmap/`), audio, and raw `assets` are physically purged from the outer ZIP, retaining only system XMLs and the desktop launcher icon.
* **Transparent Runtime Asset Redirection**: Purged assets are encrypted into an encrypted archive and mounted dynamically during Application and Service startup by patching `Resources` and `AssetManager`, allowing original `R.layout.xxx` or `R.drawable.xxx` calls to function seamlessly.
* **Image Perceptual Hash Cleansing**: Embedded image resamplers optimize and smooth oversized static images, disrupting their invariant cryptographic hashes (SHA256) and perceptual hashes (pHash) to evade static visual signature detection.

### 2.4 Sensitive Component Desensitization & AV False-Positive Elimination
* **High-Risk Accessibility Service Disguise**: Circumvents antivirus heuristics that flag accessibility services (e.g., `BackAccess*`) paired with SMS permissions (`SEND_SMS`) as Trojans by dynamically obfuscating and desensitizing sensitive service class names.
* **System Settings Virtualization Hook**: Intercepts `Settings.Secure.getString("enabled_accessibility_services")` calls in the stub layer, ensuring that internal authorization checks align seamlessly with system accessibility states while eliminating AV detection.

### 2.5 32MB+ Manifest Inflation Anti-Decompilation Traps (Optional)
* **Zero-Loss Chunk Inflation**: Exploits the AOSP C++ `ResXMLTree` behavior where unknown chunks are safely skipped via pointer addition, embedding 32MB+ zero-padded chunks and high-entropy noise chunks into `AndroidManifest.xml`.
* **Reverse Engineering Tool & Sandbox Denial-of-Service**: While the final compressed APK size increases by only a few dozen kilobytes, unpacking the manifest expands it to over 33MB, instantly triggering Out-Of-Memory (OOM) crashes or Zip Bomb thresholds in Jadx, Apktool, GDA, and AV cloud sandboxes.

### 2.6 ZIP Alignment & Multi-Channel Normalized Signing
* **Full V1/V2 Signing Support**: Integrates standard Android signing schemes to meet signature verification standards on Android 7.0 through 14.
* **4-Byte ZipAlign Optimization**: Enforces strict 4-byte (32-bit) alignment for native shared libraries and uncompressed resources, ensuring fast memory mapping and minimal RAM consumption on physical devices.

---

## 3. Web Console Configuration & Management

The hardening dashboard provides fine-grained control for various application scenarios:

| Option | Recommended | Description |
| :--- | :---: | :--- |
| **Enable Hardening** | Enabled (Mode 2) | Activates dynamic DEX encryption and native stub hardening |
| **Asset Encryption** | Enabled | Physically strips outer resources/layouts and executes from encrypted virtual assets |
| **Manifest Sanitization**| Enabled | Activates Scheme 1 to strip outer business components and prevent static analysis |
| **Manifest Inflation** | Optional | Injects 32MB+ AXML expansion traps to disrupt decompilers and cloud sandboxes (Default: Disabled) |
| **Pseudo-Encryption / Align** | Enabled | Disrupts standard unzippers and enforces 4-byte memory alignment |

---

## 4. Key Advantages & Business Value

1. **Fully Automated Pipeline**: Supports web-based single-package hardening, batch tasks, and API integration. Hardening, signing, and alignment are executed in a single automated step.
2. **Zero Source Code Intrusion**: Operates directly on standard Release APKs with no modification required to client source code.
3. **Flawless ROM Compatibility**: Deeply tuned for custom Android distributions, eliminating common post-hardening pitfalls such as accessibility crashes, foreground notification exceptions, and deep reflection blocks.
4. **Resilient Offense-Defense Balance**: Offers high-strength anti-reverse engineering capabilities alongside adaptable evasion and anti-sandbox configurations to protect applications in production.

## Contact Us
![Contact Us](qrcode.png)

[Click to contact us](http://47.108.138.179:8006/?session=0b54fbc324904420)