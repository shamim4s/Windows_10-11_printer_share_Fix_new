▶️ How to Run (One-Line Command)
Step 1: Open PowerShell

Press Win + X

Select Windows PowerShell (or Terminal)

❗ You do NOT need to open PowerShell as Administrator.
The command will request elevation automatically.

Step 2: Copy & Paste the Command Below
powershell -Command "Start-Process cmd.exe -Verb RunAs -ArgumentList '/c reg add \"HKLM\SOFTWARE\Policies\Microsoft\Windows NT\Printers\RPC\" /v RpcUseNamedPipeProtocol /t REG_DWORD /d 1 /f & reg add \"HKLM\SOFTWARE\Policies\Microsoft\Windows NT\Printers\RPC\" /v RpcProtocols /t REG_DWORD /d 0x7 /f & reg add \"HKLM\SOFTWARE\Policies\Microsoft\Windows NT\Printers\RPC\" /v ForceKerberosForRpc /t REG_DWORD /d 1 /f & reg add \"HKLM\System\CurrentControlSet\Control\Print\" /v RpcAuthnLevelPrivacyEnabled /t REG_DWORD /d 0 /f & reg add \"HKLM\SYSTEM\CurrentControlSet\Services\LanmanWorkstation\Parameters\" /v AllowInsecureGuestAuth /t REG_DWORD /d 1 /f & powershell Set-SmbClientConfiguration -RequireSecuritySignature $false -Force & powershell Set-SmbClientConfiguration -EnableInsecureGuestLogons $true -Force & wusa /uninstall /kb:5072033 /quiet /norestart'"

Step 3: Accept UAC Prompt

A User Account Control dialog will appear

Click Yes

All commands will now run automatically in an elevated session.

✅ What This Command Does

Adds multiple registry keys under:

HKLM\SOFTWARE\Policies\Microsoft\Windows NT\Printers\RPC

HKLM\SYSTEM\CurrentControlSet\Control\Print

HKLM\SYSTEM\CurrentControlSet\Services\LanmanWorkstation

Modifies SMB client configuration

Enables insecure guest logons

Uninstalls Windows Update KB5072033

Runs everything in a single elevated execution

🔄 Reboot Recommendation

After execution, restart the system to ensure all changes take effect.

shutdown /r /t 0

🧪 Tested Environment

Windows 10 x64

Windows 11 x64

❓ Troubleshooting

UAC prompt doesn’t appear
→ Ensure you are not already in a restricted environment (e.g. kiosk mode)

Command window closes immediately
→ This is expected behavior when execution completes successfully

Update uninstall fails
→ The update may already be removed or not installed

📌 Disclaimer

Use at your own risk.
The author is not responsible for system instability or security exposure.
