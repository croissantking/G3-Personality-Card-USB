# G3-Personality-Card-USB

Various Personality cards that are installed in the Beige G3's PERCH slot have footprints for a single USB 1.0/1.1 socket and supporting circuitry, similar to that found on USB PCI cards with a Firelink chip. This USB footprint is found on the second revision of the Whisper and Wings cards. The rare Bordeaux card has also been seen with the footprint and supports a dual USB port header.

Prototype machines exist with onboard USB on their Personality card, but no production machines ever had it installed. It's not clear if it was at one point planned for the Beige to have built-in USB, or if the footprint was meant solely for development.

I have a soft spot for the Beige G3 and was thrilled to find it has this 'secret', hidden feature and given nobody else has tried to get it working I jumped in. I initially soldered in a CMD 0670 chip taken from a donor PCI card, and, with the help of other forum members at 68kMLA, I worked out the values of the capacitors and resistors that are required to get the USB circuitry working. Other key components included a 5V oscillator, a polyfuse and of course the USB port itself.

Included in this repository are KiCad schematic files for Whisper and Wings cards.

You can read about my journey here: https://68kmla.org/bb/index.php?threads/getting-g3-whisper-perch-usb-working.43681/

Hackaday also wrote an article about this project: https://hackaday.com/2023/04/01/apple-never-gave-them-usb-now-theyre-getting-it-for-themselves/

So far, testing has shown the USB portion of the Personality card to be fully functional and reliable under Mac OS 9.2.2 and Mac OS X 10.2.8. It's seen as a PCI card in slot 'PERCH' and therefore relies on the same drivers (and has the same limitations) as a traditional USB OHCI PCI card would.

I have successfully tested a CMD0670B-400 and an Opti Firelink 82c861. To use the Firelink, a small adjustment to the published schematics is required when populating the board: PWRFLT1 must be tied to +5V. This can be achieved by bridging U9 pin 16 to pin 2 with a 10K resistor. The Firelink will fail to initialize if PWRFLT1 is left floating, which is interestingly not an issue with the 0670.

One of the more difficult tasks of the modification is creating an opening on the metal backplate of the Personality card to allow USB devices to plug in. My method is to mark out the opening and then stitch-drill and file from the inside.

Future goals:

– Get the the Unitrode power supply section working, which is more reliable than a fuse.
– Get the USB keyboard power on circuitry working.

Peter Baran (@croissantking)

--

Update History:

24/5/2023 Uploaded schematic Rev 1, PDF and BOM.

12/7/2023 Updated schematic to Rev 2. Corrected some minor errors and made it clearer where the different circuits are.

3/7/2024 Updated the readme to explain what's needed to get the Firelink chip to work.

21/7/2024 Updated the Whisper schematic to V3, which includes layout improvements as well as worked out values for the Unitrode and power-on circuits, although they are not yet tested. Also uploaded a brand new Wings V1 schematic. Updated the readme accordingly.
