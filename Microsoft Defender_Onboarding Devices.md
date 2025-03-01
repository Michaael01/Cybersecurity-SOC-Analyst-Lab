# Onboarding a windows device
1. In the Defender XDR portal, in the left navigation menu, scroll down, expand the System section , select Settings , then on the Settings page, select Endpoints.
2. Select Onboarding in the Device Management section.

Tip: You can also perform device onboarding in the Resources section of the left menu bar. Expand Resources and select Devices. On the Device Inventory page, with PCs and Mobiles selected, scroll down to Onboard Devices. This will take you to the Settings > Endpoints page .

3. In the "1. When onboarding a device area set the Deployment Method drop-down menu to "Local Script (for up to 10 devices)" and select the Download Onboarding Package button . ![GitHub Logo](https://media-hosting.imagekit.io//691820e75b8e460f/onboarding%20package.png?Expires=1835433296&Key-Pair-Id=K2ZIVPTIP2VGHC&Signature=z4TuqZfdmqoR78WkzBhyUFMbwWRMu54RSKNSFVVS0tbc2THkN12HKspv6U-~qc1tx5jUs7OErQNyzJco2mE-a33vHqr0iVffbxTMIQBvg2eswyxWeqD-CBDUtM1h6yJOPya8XV2OwRftYYDoH-DZX9aCiZ5hDD8w7flOylQidLDKq6g7nG7NW75g4mQHXD-nUcD0ZE92SRueCR7o4J87Mo65FJTDFuISxcz74e6TslRS0toalV3uHsrcAQWz4fyLpmMt05M6fc9--a2Q3MYa1oCuykiCKE5hje5-ZIPo9BrNtPlIFLO7H4c-zi9gUqb85UxpDoOeM3f2jlkZ8CYxiA__)
4. In the Downloads pop-up window , highlight the "WindowsDefenderATPOnboardingPackage.zip" file with your mouse and select the folder icon** Show in folder**. Tip: In case you don't see it, check the c:\users\admin\downloads directory.
5. Right-click the downloaded ZIP file and select Extract All... , make sure Show extracted files when complete is checked, and select Extract .



Tip: If your browser is blocking the download, take an action in the browser to allow the download. In the Microsoft Edge browser, you may see the message " WindowsDefenderATPOnboardingPackage.zip does not download normally. Make sure you trust... , select the ellipsis (...) button if necessary, and then select Keep . In Microsoft Edge, a second pop-up appears with the message " Make sure you trust WindowsDefenderATPOnboardingPackage.zip before opening it ," select Show more to expand the selections, and select Keep anyway.

6. Right-click the extracted file "WindowsDefenderATPLocalOnboardingScript.cmd" and select Properties . Select the Unblock checkbox at the bottom right of the Properties windows and select OK .
7. Right-click the extracted "WindowsDefenderATPLocalOnboardingScript.cmd" file again and choose Run as administrator . Tip: If you encounter the Windows SmartScreen window, select More info and choose Run anyway. ![GitHub Logo](https://media-hosting.imagekit.io//30d939c76da4401c/onboarding%20a%20device.png?Expires=1835434290&Key-Pair-Id=K2ZIVPTIP2VGHC&Signature=Dm0jWuqfWvMd4xOHcXS6mDt9vAvIUnZShHJJo~j0xyv1oogtEdkoHSLjS-LqYEqaE3p-XPqB~8wnC6xuqRsPyNWnB2QO6x65kwbAYnV6jl0K9iZWH0k2bleYFiY4oZLyr9jyG6dPQZL5mtl65O7wEUBqR3dnVVCpEk9y-KwYRLNxckgp~QHwFAw4LR8-QLXn0WHz-Z-AzJU~6vBPhpJf2gs9afuNk4aSpQ5u~SOGz1hakJiwg23~AaOnISwS9LerxRweAlF7jN-bUJxG3yOik3bhalp2egpu490nIHUrDZigtkhs-r50XZZpPWpNZoRMpzklErKCUw~E5I6ZDD0Wmg__)
8. When the "User Account Control" window appears, select Yes to allow the script to run and answer Y to the question presented by the script, and press Enter . When you're done, you should see a message on the command screen that says Machine successfully onboarded to Microsoft Defender for Endpoints.
9. Press any key to continue. This closes the Command Prompt window.

## Run a detection test
1. To verify that the device is properly onboarded and reporting to the service,run the detection script on the newly onboarded device:

a. Open a Command Prompt window
b. At the prompt, copy and run the command below. The Command Prompt window will close automatically. powershell.exe -NoExit -ExecutionPolicy Bypass -WindowStyle Hidden $ErrorActionPreference= 'silentlycontinue';(New-Object System.Net.WebClient).DownloadFile('http://127.0.0.1/1.exe', 'C:\\test-WDATP-test\\invoice.exe');Start-Process 'C:\\test-WDATP-test\\invoice.exe'
