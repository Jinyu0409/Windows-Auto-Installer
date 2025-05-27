# Windows-Auto-Installer
Tools used to automatically install Windows

1. **In-depth integration of naming rules**

- Adopt the structure of "System_Version_Architecture_Language_Features"

- Key parameters are extracted from the download link metadata

- Example: `Win10_22H2_19045.5198_AIO_x64_ZH-CN_2024-11.iso`

2. **Intelligent document management**

- Conflict handling: automatic renaming/breakpoint continuation

- Timestamp addition: Automatically add the suffix `-YYYYMMDD-HHMM` after the download is completed

- Version information preview: display mirror details before downloading

3. **PE environment optimization**

- Multi-threading download: priority to use aria2c (speed 3-5 times faster)

- Dynamic disk allocation: automatically find available drive mounting

- RAM disk support: accelerate temporary operation

4. **Data enhancement**

- The build version number directly embeds the document name (such as 19045.5198)

- Mark the special version type (AIO/ESD/OEM)

- Contains MSDN original release code (such as GRC1CULFRER)

### Instructions for use

1. **Preparation for the first operation**

```cmd

:: Initialize the working environment in PE

Wpeutil InitializeNetwork

Mkdir X:\WinDeploy

```

2. **Typical operation process**

```cmd

1. Choose to download Windows 11 mirror images

2. Automatic naming: Win11_23H2_22631.4123_Consumer_x64_ZH-CN_DVD.iso

3. Use aria2c multi-threed download (automatic retry mechanism)

4. Timestamp will be added automatically after the download is completed:

→ Win11_... _DVD-20240115-1430.iso

5. Hount to the first available drive (such as V:)

6. Run V:\sources\setup.exe

```

3. **Advanced verification function**

```cmd

:: Automatically generate verification documents after the download is completed

Certutil -hashfile "%ISO_FILE%" SHA256 > "%ISO_FILE%.sha256"

```

The Script Has Achieved The Deep Integration Of Naming Rules And Functional Logic. It Is Recommended To Deploy It After Testing And Verification In The Actual PE Environment.
