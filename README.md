# G3-Personality-Card-USB

Later revisions of the Personality card that come with every Beige G3 have footprints for a single/dual USB 1.1 socket and supporting circuitry, similar to that found on early USB PCI cards. There are three types of Personality card - the Whisper, the Wings, and the Bordeaux; all three potentially have the footprint.

Prototype machines have been seen with this USB socket, but no production machines ever had it installed. It's not clear if it was at one point planned for the Beige to have built-in USB, or if the footprint was meant solely for development.

I have a soft spot for the Beige G3 and was thrilled to find it has this 'secret', hidden feature and given nobody else has tried to get it working I jumped in. I initially soldered in a CMD 0670 chip taken from a donor PCI card, and, with the help of other forum members at 68kMLA, I worked out the values of the capacitors and resistors that are required to get the USB circuitry working. Other key components included a 5V oscillator, a polyfuse and of course the USB port itself.

Included in this repository are the schematic files I drew up in KiCad for my Whisper card.

You can read about my journey here: https://68kmla.org/bb/index.php?threads/getting-g3-whisper-perch-usb-working.43681/

Hackaday also wrote an article about this project: https://hackaday.com/2023/04/01/apple-never-gave-them-usb-now-theyre-getting-it-for-themselves/

So far, testing has shown the USB portion of the Personality card to be fully functional and reliable under Mac OS 9.2.2 and Mac OS X 10.2.8. It's seen as a PCI card in slot 'PERCH' and therefore relies on the same drivers (and has the same limitations) as a traditional USB OHCI PCI card would.

I have successfully tested a CMD0670B-400 and an Opti Firelink 82c861. To use the Firelink, a small adjustment to the published schematics is required when populating the board: PWRFLT1 must be tied to +5V. This can be achieved by bridging U9 pin 16 to pin 2 with a 10K resistor. The Firelink will fail to initialize if PWRFLT1 is left floating, which is interestingly not an issue with the 0670.

Peter Baran (@croissantking)

--

Update History:

24/5/2023 Uploaded schematic Rev 1, PDF and BOM.

12/7/2023 Updated schematic to Rev 2. Corrected some minor errors and made it clearer where the different circuits are.

3/7/2024 Updated the readme to explain what's needed to get the Firelink chip to work.
