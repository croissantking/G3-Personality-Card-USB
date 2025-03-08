# G3 Personality Card USB

<b>Outline</b>
<br><br>
Various Personality cards that are installed in the Beige G3 PERCH slot have footprints for a single USB 1.0/1.1 socket and supporting circuitry, similar to that found on USB PCI cards with a FireLink chip. This footprint is found on later revisions of the Whisper and Wings A/V cards. The rare Bordeaux DVD Video card has also been seen with the footprint and appears to support either a single or dual USB port header.
<br><br>
<img src="https://github.com/user-attachments/assets/53ae1407-8808-47af-b2a3-14ff611aa877" width=50% height=50%>
<br><br>
Prototype machines exist with onboard USB on their Personality card, but no production machines ever had it installed. It's not clear if it was at one point planned for the Beige to have built-in USB, or if the footprint was meant solely for development.
<br><br>
I have a soft spot for the Beige G3 and was thrilled to find it has this 'secret', hidden feature and given nobody else has tried to get it working I jumped in. I initially soldered in a CMD 0670 chip taken from a donor PCI card, and, with the help of other forum members at 68kMLA, I worked out the values of the capacitors and resistors that are required to get the USB circuitry working. Other key components included a 5V oscillator, a polyfuse and of course the USB port itself.
<br><br>
<b>Modification</b>
<br><br>
Included in this repository are KiCad schematic files and BOMs for Whisper and Wings cards. The easiest way to get started is to follow the links below to order the Mouser projects I've created, then assemble your card using the BOM to help you. You will need a donor PCI card to take the USB controller chip from.
<br><br>
You can install either a CMD0670B-400 or an OPTi FireLink 82C861 chip. To use the Firelink, a small adjustment to the published schematics is required when populating the board: PWRFLT1 must be tied to +5V. This can be achieved by locating the IC footprint for U9 (Whisper) or U19 (Wings A/V) and bridging pins 15 and 16 with a 10K resistor. The Firelink will fail to initialize if PWRFLT1 is left floating, which is not an issue with the 0670.
<br><br>
<img src="https://github.com/user-attachments/assets/67582955-f98a-45d6-b35d-814bbac82cdf" width=60% height=60%>
<br><br>
One of the more difficult tasks of the mod is creating an opening on the metal backplate to allow USB devices to plug in. My method is to mark out the opening and then stitch-drill and file from the inside.
<br><br>
<img src="https://github.com/user-attachments/assets/5f7984d2-c3b9-444d-9f46-8d9881c3f743" width=50% height=50%>
<img src="https://github.com/user-attachments/assets/34577bb2-c02f-48b2-8956-6d64bfce31a1" width=50% height=50%><br><br>
So far, testing has shown the USB interface to be fully functional and reliable under Mac OS 9.2.2 and Mac OS X 10.2.8. It's seen as a PCI card in slot 'PERCH' and therefore relies on the same drivers as a traditional USB OHCI PCI card would.
<br><br>
<img src="https://github.com/user-attachments/assets/df3014ed-af30-4027-9707-704015e1fdd0" width=60% height=60%>
<br><br>
<b>Startup Circuit</b>
<br><br>
A startup circuit exists as part of the USB footprint. It's optional, but if populated you will be able to start up your Beige G3 with the power key on an Apple USB keyboard. This is tested and confirmed working.<br><br>
<b>Files and Project Links</b>



<table><thead>
  <tr>
    <th></th>
    <th>PDF</th>
    <th>BOM*</th>
    <th>Mouser Cart*</th>
  </tr></thead>
<tbody>
  <tr>
    <td>Whisper</td>
    <td><a href="https://github.com/croissantking/G3-Personality-Card-USB/blob/main/Whisper/Whisper%20USB%20V4.pdf" target="_blank" rel="noopener noreferrer">Whisper USB V4.pdf</a></td>
    <td><a href="https://github.com/croissantking/G3-Personality-Card-USB/blob/main/Whisper/Whisper%20USB%20BOM.csv" target="_blank" rel="noopener noreferrer">Whisper USB BOM.csv</a></td>
    <td><a href="https://www.mouser.co.uk/api/CrossDomain/GetContext?syncDomains=www&returnUrl=https%3a%2f%2fwww.mouser.com%2fProjectManager%2fProjectDetail.aspx%3fAccessID%3ded20c4f711&async=False&setPrefSub=False&clearPrefSub=False" target="_blank" rel="noopener noreferrer">CK's Whisper USB Mod</a></td>
  </tr>
  <tr>
    <td>Wings A/V</td>
    <td><a href="https://github.com/croissantking/G3-Personality-Card-USB/blob/main/Wings/Wings%20USB%20V2.pdf" target="_blank" rel="noopener noreferrer">Wings USB V2.pdf</a></td>
    <td><a href="https://github.com/croissantking/G3-Personality-Card-USB/blob/main/Wings/Wings%20USB%20BOM.csv" target="_blank" rel="noopener noreferrer">Wings USB BOM.csv</a></td>
    <td><a href="https://www.mouser.co.uk/api/CrossDomain/GetContext?syncDomains=www&returnUrl=https%3a%2f%2fwww.mouser.com%2fProjectManager%2fProjectDetail.aspx%3fAccessID%3d3c8a106edf&async=False&setPrefSub=False&clearPrefSub=False" target="_blank" rel="noopener noreferrer">CK's Wings USB Mod</a></td>
  </tr>
</tbody></table>

*Note that the base USB mod and startup circuit have now been combined into one list. 

<br>
  <b>Further Reading</b>
<br><br>
You can read about my journey here: https://68kmla.org/bb/index.php?threads/getting-g3-whisper-perch-usb-working.43681/
<br><br>
Hackaday also wrote an article about this project: https://hackaday.com/2023/04/01/apple-never-gave-them-usb-now-theyre-getting-it-for-themselves/
<br><br>
<b>Future goals</b>
<br><br>
– Get the the Unitrode power supply section working, this is the chip which would sit at U9/U19, and is a more reliable alternative than a fuse.<br>
– Draw up schematics for a Bordeaux card with an option for dual ports.
<br><br><br>
<b>Peter Baran (@croissantking)</b>

<br><br>
--
<b>Update History</b>
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
<br><br>
28/7/2024 Added a new USB BOM for the Wings card, and startup circuit BOMs for both cards. Added links to Mouser projects in this readme.
<br><br>
8/3/2025 Combined BOMs and Mouser carts for base mod and startup circuits. Updated the Readme with a couple of new photos and a table which makes it easier to locate all the relevant files.
