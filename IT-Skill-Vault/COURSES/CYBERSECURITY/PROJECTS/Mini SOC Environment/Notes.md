
## Simple SOC Mental Model

**WHO → DID WHAT → USING WHICH PROGRAM → FROM WHERE**

****
## Basic Splunk Fields
#### Image (WHAT ran)

Example:

```
C:\Windows\System32\cmd.exe
```

👉 This tells you: “What program was executed”

#### CommandLine (WHAT it did)

Example:

```
cmd.exe /c ipconfig
```

👉 This tells you: “What the program actually ran”

#### ParentImage (WHO launched it)

Example:

```
explorer.exe
```

👉 This tells you: “What started this process”
> 
#### User (WHO did it)

Example:

```
DESKTOP-XXX\User
```


#### EventCode (WHAT type of event)

Common ones:

|EventCode|Meaning|
|---|---|
|1|Process created|
|3|Network connection|
|11|File created|

****

### Learn the important Sysmon Event IDs

You'll investigate:

- Event ID 1 – Process Creation
- Event ID 3 – Network Connection
- Event ID 11 – File Creation
- Event ID 7 – Image Loaded
- Event ID 13 – Registry Value Set