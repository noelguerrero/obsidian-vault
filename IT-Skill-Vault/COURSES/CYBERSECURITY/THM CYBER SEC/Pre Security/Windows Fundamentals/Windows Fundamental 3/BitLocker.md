
What is **BitLocker**?
is a **full-disk encryption** feature in Windows that protects your data by encrypting your drives.

Per Microsoft, "_BitLocker Drive Encryption is a data protection feature that integrates with the operating system and addresses the threats of data theft or exposure from lost, stolen, or inappropriately decommissioned computers_".

Per Microsoft, "_BitLocker provides the most protection when used with a Trusted Platform Module (TPM) version 1.2 or later. The TPM is a hardware component installed in many newer computers by the computer manufacturers. It works with BitLocker to help protect user data and to ensure that a computer has not been tampered with while the system was offline_".

## Bitlocker and TPM relationship

**Bitlocker** - is the lock that encrypt the drive and give the key into TPM.
**TPM** - stores the key that Bitlocker needed

**In one sentence:** BitLocker encrypts your data, and TPM makes sure only your trusted system can unlock it.

### How BitLocker + TPM work together (step by step)

1. **BitLocker encrypts your drive**
    - Your files are encrypted using an encryption key
2. **TPM securely stores the key**
    - The key is locked inside the TPM
    - It cannot be extracted in plain form
3. **System boots**
    - TPM checks the boot environment (UEFI, bootloader, firmware)
4. **If everything is trusted**
    - TPM releases the key automatically
    - Windows boots normally (no password needed)
5. **If something changes**
    - Example: bootloader modified, drive moved to another PC
    - TPM refuses to release the key
    - BitLocker asks for the **48-digit recovery key**
