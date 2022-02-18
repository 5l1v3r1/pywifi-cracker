# pywifi-cracker
Wifi -Hacking using PyWifi 🔐
Tighten Your seatbelt 🤘

Lets start with a bit of theory and module →

You must have python3.6 or python3.7 installed in your computers.

Pywifi → This module provides a cross-platform Python module for manipulating wireless interfaces.
You can install by → pip install pywifi
and read about it here → https://github.com/awkman/pywifi/blob/master/DOC.md

Wifi profiles are saved in xml format in our computers and also their is a procedure which we need to follow in order to add new profiles and connect to any profile.
Here Profile means your wifi profile i.e → ssid and other information needed by your computer to connect to wifi.

This is a brute force method so it takes large amount of time depending upon how much information you have about key and length of password wordlist.
Lets Begin the explanation→

client_ssid → name of your wifi network that you want to hack
path_to_file → path to python wordlist containing password
You can use your own python wordlist depending upon information you have about password.
If you don’t know how to create follow → https://rsajal.medium.com/python-wordlist-for-brute-force-password-cracking-9a8c62170bd2

These are color variables you don’t need to change them they are initialized to make command prompt look fancy and interactive we will see how later.

In this part we are initializing the piwifi module so that we can interact with the wifi interface from computer

argparse → This module is used for making command line interactive.
You can read about it from official tutorial here →
https://docs.python.org/3/howto/argparse.html

So basically we are trying to pass two important variables client_ssid and path_to_file by hard-coding or by command line depending upon the use.

If you want to pass by Command Line Your syntax will go somewhat like →

python3 pywifi_medium.py -s NAME_OF_WIFI -w PATH_TO_PASSWORD_LIST

if you want to hardcode it → go by changing client_ssid and wordlist path variable.

In this part we taking arguments from command line in args and checking if user has given them from command line . If not take the one from hard code

Then we are trying to find file and cracking the wifi password

This part opens the file and fetches each word written in it and send it to main function.

THE MAIN FUNCTION →

As the name suggests this function is main culprit of the process. Main function requires three things → password, number , ssid which are send from pwd function .Then we are creating the profile that would be compatible with our operating system which looks like →

<?xml version="1.0"?>
<WLANProfile xmlns="http://www.microsoft.com/networking/WLAN/profile/v1">
 <name>Dfone</name>
 <SSIDConfig>
  <SSID>
   <hex>ssid_in_hexadecimal_form</hex>
   <name>ssid_in_english</name>
  </SSID>
 </SSIDConfig>
 <connectionType>ESS</connectionType>
 <connectionMode>auto</connectionMode>
 <MSM>
  <security>
   <authEncryption>
    <authentication>Mode_of_cipher</authentication>
    <encryption>AES</encryption>
    <useOneX>false</useOneX>
   </authEncryption>
   <sharedKey>
    <keyType>passPhrase</keyType>
    <protected>true</protected>
    <keyMaterial>F175B32D4D10562D19715079CE9E1FE7E18BCA5E5586E43EC69B3B5F42ACAD000000000E80000000020000200000000EB3E8631D76E5B4E1219C15</keyMaterial>
   </sharedKey>
  </security>
 </MSM>
 <MacRandomization xmlns="http://www.microsoft.com/networking/WLAN/profile/v3">
  <enableRandomization>false</enableRandomization>
  <randomizationSeed>285113171</randomizationSeed>
 </MacRandomization>
</WLANProfile>

This is what module creates as profile. You don’t have to worry about it.
keymaterial will change as password changes and it will try to connect you to wifi.

So this was end of article.
You were really a patient audience.

Thank You !
