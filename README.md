
---

# Write-up : 

- **Platform:**  Try Hack Me   
- **Challenge Gategory:** Open-Source Intelligence    
- **Challenge Level:** Beginner  
- **Challenge Name:** OhSINT  
- **Challenge Link:** [challenge link](https://tryhackme.com/room/ohsint)   
- **Challenge Subject:**  What information can you possible get with just one image file?

---

<br>First, I downloaded the image file. Then, I analyzed this image to extract data from it. For this analysis, I used a tool called ExifTool, which checked the metadata of the file.

---

<br>

**check if exiftool is installed**
```
exiftool --version
```
<br>

**if ! installed :**
```
sudo apt install exiftool
```
---
<br>

**check the type of file :**
```
file WindowsXP.jpg
```
**expected output :**
```
WindowsXP.jpg: JPEG image data, baseline, precision 8, 1920x1080, components 3
```
### apply this command on file (image):###
```
exiftool ohsint.png
```

<br>

>Initial expected output :

```
┌──(acnr㉿kali)-[~/Desktop/thm_challenges/osint/OhSINT]
└─$ exiftool WindowsXP_1551719014755.jpg

ExifTool Version Number         : 12.16
File Name                       : WindowsXP_1551719014755.jpg
Directory                       : .
File Size                       : 229 KiB
File Modification Date/Time     : 2021:05:01 06:06:48-04:00
File Access Date/Time           : 2021:05:01 06:06:52-04:00
File Inode Change Date/Time     : 2021:05:01 06:06:52-04:00
File Permissions                : rw-r--r--
File Type                       : JPEG
File Type Extension             : jpg
MIME Type                       : image/jpeg
ExifTool                         : ExifTool 11.27
GPS Latitude                    : 54 deg 17' 41.27" N
GPS Longitude                   : 2 deg 15' 1.33" W
Copyright                       : 0woodflint
Image Width                     : 1920
Image Height                    : 1080
Encoding Process                : Baseline DCT, Huffman coding
Bits Per Sample                 : 8
Color Components                : 3
Y Cb Cr Sub Sampling            : YCbCr4:2:0 (2 2)
Image Size                      : 1920x1080
Megapixels                      : 2.1
GPS Latitude Ref                : North
GPS Longitude Ref               : West
GPS Position                    : 54 deg 17' 41.27" N, 2 deg 15' 1.33" W

```

**From the image data i obtained the name of person : "**0woodflint**"**
```
Copyright                       : 0woodflint
```


### Investigating the Name ###

**I pasted the name into the search field of web browser :**

![screen](files/Screen_1_.png)

### I obtained some information, such as his GitHub and Twitter (X) profiles:
```
    > From github : 
        - City [Q2]
        - Email[Q4],[Q5]
        - Wordpress

    > From wordpress :
        - Holiday [Q6]
        - Password [Q7] 

    > From twitter X :
        - Avatar [Q1]
        - BSSID [Q3]

Password: I inspected the web page source code and found a hidden text in the same color as the page background

BSSID: From the BSSID, I determined the corresponding SSID using wigle.net.

```
---

## Questions / Answers : 

### Q1 - What is this user's avatar of?  
<details><summary>click to see the answer</summary>cat</details>

### Q2 - What city is this person in?
<details><summary>click to see the answer</summary>London</details>

### Q3 - What is the SSID of the WAP he connected to?
<details><summary>click to see the answer</summary>UnileverWiFi</details>

### Q4 - What is his personal email address?
<details><summary>click to see the answer</summary>OWoodflint@gmail.com</details>

### Q5 - What site did you find his email address on?
<details><summary>click to see the answer</summary>Github</details>

### Q6 - Where has he gone on holiday?
<details><summary>click to see the answer</summary>New York</details>

### Q7 - What is the person's password?
<details><summary>click to see the answer</summary>pennYDr0pper.!</details><br>

---

<br><br>

---

>BSSID:

    The MAC address identifier of a Wi-Fi access point’s radio (e.g. 00:11:22:33:44:55).
    Use to uniquely identify a specific AP (vs SSID which can be shared).

>SSID:

    The network name broadcast by a Wi-Fi network (e.g. CoffeeShop_WiFi).
    Human-readable; many APs can share the same SSID.

>WAP (Wireless Access Point):

    The device that provides Wi-Fi network access (router or dedicated AP).
    May host one or more BSSIDs (radios/SSs) and advertise one or more SSIDs.

>exiftool:

    Command-line tool to read/write metadata from images, audio, video, PDFs, etc.

>wigle.net:

    Crowdsourced database & map of Wi-Fi networks (SSIDs/BSSIDs + locations) collected by users.
    Use cases: site surveys, defensive checks (find exposed APs), OSINT research.
    Privacy/legal note: contains geolocated network identifiers — use ethically and follow laws/terms.

---

<br>

>This Write-up is written by @achnouri

