# G3 Personality Card USB

**Outline**
<br><br>
Various Personality cards that are installed in the Beige G3 PERCH slot have footprints for a single USB 1.0/1.1 socket and supporting circuitry, similar to that found on USB PCI cards with a FireLink chip. This footprint is found on later revisions of the Whisper and Wings A/V cards. The rare Bordeaux DVD Video card has also been seen with the footprint and appears to support either a single or dual USB port header.
<br><br>
<img src="https://github.com/user-attachments/assets/53ae1407-8808-47af-b2a3-14ff611aa877" width=50% height=50%>
<br><br>
Prototype machines exist with onboard USB on their Personality card, but no production machines ever had it installed. It's not clear if it was at one point planned for the Beige to have built-in USB, or if the footprint was meant solely for development.
<br><br>
I have a soft spot for the Beige G3 and was thrilled to find it has this 'secret', hidden feature and given nobody else has tried to get it working I jumped in. I initially soldered in a CMD 0670 chip taken from a donor PCI card, and, with the help of other forum members at 68kMLA, I worked out the values of the capacitors and resistors that are required to get the USB circuitry working. Other key components included a 5V oscillator, a polyfuse and of course the USB port itself.
<br><br>
You can read about my journey here: https://68kmla.org/bb/index.php?threads/getting-g3-whisper-perch-usb-working.43681/
<br><br>
Hackaday also wrote an article about this project: https://hackaday.com/2023/04/01/apple-never-gave-them-usb-now-theyre-getting-it-for-themselves/
<br><br>
**Modification**
<br><br>
Included in this repository are KiCad schematic files for Whisper and Wings cards.
<br><br>
So far, testing has shown the USB portion of the Personality card to be fully functional and reliable under Mac OS 9.2.2 and Mac OS X 10.2.8. It's seen as a PCI card in slot 'PERCH' and therefore relies on the same drivers (and has the same limitations) as a traditional USB OHCI PCI card would.
<br><br>
<img src="https://github.com/user-attachments/assets/df3014ed-af30-4027-9707-704015e1fdd0" width=60% height=60%>
<br><br>
I have successfully tested a CMD0670B-400 and an OPTi FireLink 82c861. To use the Firelink, a small adjustment to the published schematics is required when populating the board: PWRFLT1 must be tied to +5V. This can be achieved by bridging U9 pin 16 to pin 2 with a 10K resistor. The Firelink will fail to initialize if PWRFLT1 is left floating, which is interestingly not an issue with the 0670.
<br><br>
One of the more difficult tasks of the mod is creating an opening on the metal backplate to allow USB devices to plug in. My method is to mark out the opening and then stitch-drill and file from the inside.
<br><br>
<img src="https://github.com/user-attachments/assets/34577bb2-c02f-48b2-8956-6d64bfce31a1" width=50% height=50%><br><br>
**Startup Circuit**<br><br>
A startup circuit exists as part of the USB footprint. It's optional, but if populated you will be able to start up your Beige G3 with the power key on an Apple USB keyboard. This is tested and confirmed working.<br><br>
**Mouser Project Links**
<br><br>
[Whisper USB Mod](https://www.mouser.co.uk/api/CrossDomain/GetContext?syncDomains=www&returnUrl=https%3a%2f%2fwww.mouser.com%2fProjectManager%2fProjectDetail.aspx%3fAccessID%3ded20c4f711&async=False&setPrefSub=False&clearPrefSub=False)
<br>
[Whisper Startup Circuit](https://www.mouser.co.uk/api/CrossDomain/GetContext?syncDomains=www&returnUrl=https%3a%2f%2fwww.mouser.com%2fProjectManager%2fProjectDetail.aspx%3fAccessID%3d3795cb82c2&async=False&setPrefSub=False&clearPrefSub=False)
<br><br>
[Wings USB Mod](https://www.mouser.co.uk/api/CrossDomain/GetContext?syncDomains=www&returnUrl=https%3a%2f%2fwww.mouser.com%2fProjectManager%2fProjectDetail.aspx%3fAccessID%3d3c8a106edf&async=False&setPrefSub=False&clearPrefSub=False)
<br>
[Wings Startup Circuit](https://www.mouser.co.uk/api/CrossDomain/GetContext?syncDomains=www&returnUrl=https%3a%2f%2fwww.mouser.com%2fProjectManager%2fProjectDetail.aspx%3fAccessID%3d86d3ab9abc&async=False&setPrefSub=False&clearPrefSub=False)
<br><br>
**Future goals**
<br><br>
– Get the the Unitrode power supply section working, which is a more reliable alternative than a fuse.<br>
– Draw up schematics for a Bordeaux card.
<br><br><br>
**Peter Baran (@croissantking)**

<br><br>
--
**Update History**
<br><br>
24/5/2023 Uploaded schematic Rev 1, PDF and BOM.
<br><br>
12/7/2023 Updated schematic to Rev 2. Corrected some minor errors and made it clearer where the different circuits are.
<br><br>
3/7/2024 Updated the readme to explain what's needed to get the Firelink chip to work.
<br><br>
21/7/2024 Updated the Whisper schematic to V3, which includes layout improvements as well as worked out values for the Unitrode and power-on circuits, although they are not yet tested. Also uploaded a brand new Wings V1 schematic. Updated the readme accordingly.
<br><br>
25/7/2024 Uploaded Whisper V4 and Wings V2 schematics, which includes corrections to the startup circuit, now tested and working. 
