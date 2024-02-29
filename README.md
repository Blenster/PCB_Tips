# PCB_Tips
Making a PCB? What did you forget? Use this checklist before you order and save yourself some pain and money.

Some general thoughts and considerations before sending a PCB off to the fab house based on lessons learned, often the hard way, by myself and some of my friends:

## General Tips:
- Use rounded corners and avoid sharp points
- Place your mounting holes, with screw head standoffs, BEFORE you route your traces
- Decoupling caps. You can probably use a few more
- Did you use protection diodes?
- Did you connect the programming port of the MCU to a programming header?
- Is everything labeled clearly on the silkscreen?
  - Polarities
    - LEDs
    - Diodes
    - Capacitors
    - ICs (add the notch)
    - Headers
  - Product Name
  - Company Name
  - Logos
  - URLs
  - Board version
  - Something fun, just for you
- Make sure all layers are visible before copying the board (for example making a panel)
- Do you have any high speed signals (usb 2 and up speed)? If so, make sure they don’t cross a break in the ground plane.
- Do you have any plated slots?
  - Did you draw them the way your PCB shop wants?
  - Did you make sure that their method doesn’t break your clearance checking?
- Footprints:
  - Did you print out the PCB on paper to check it against your actual parts?
  - No seriously; check those footprints against the datasheets one more time. Measure carefully!
  - Are those LEDs indicated correctly on the silkscreen? Check the datasheet again. Manufacturers aren’t consistent on marking even in the same product line sometimes.
- Do you have test points? (Power rails, logic pins, I2C/SPI/UART lines, etc)
- Did you remember to put a power or other indicator LEDs to help with debugging?
- Are your parts still available?
- Have you slept on it?

## If you’re working on a prototype:
- Use more PCB space; it’s not too expensive to do a 4x4 inch board (check your board fab house)
- Modular design:
  - Break up the layout into modular sections:
    - Power
    - Signaling
    - Logic 
    - Etc.
  - Separate parts and design it with `0 Ohm` resistors or other easy ways to break things apart if these chunks don’t work
  - Use Test Points on the input and output of these modular sections
- Got any of those pesky RX/TX pairs? Lay them out in an easy to fix configuration such as this image or by using test points and cuttable traces:
  - ![A design for resistors to be placed either up and down or left and right to connect TX and RX lines](https://cdn-blog.adafruit.com/uploads/2024/02/one-one-8-600x321.png)
- Break out unused GPIO to test pads “just in case”
- Use the most flexible options for I2C address setting that you can

## If you’re working on a final version:
- Avoid ground loops; more vias!
- Design for manufacturing/assembly
  - Can you get those plugs in on an assembly line?
  - How hard is it to fix that in the device?
  - Tall components blocking access to things?
  - Use different plug types and pin counts to make it harder to plug the wrong thing in the wrong place
  - Don’t forget to account for the shroud sizes of headers and plugs; they can be bigger than you thought.
- This is the time for smaller/more compact designs
- Can you combine BOM items (e.g. do you need a `1.1K resistor` and a `1K resistor` or can they both be `1.1k`?)
- What is the smallest component my assembly house will place before they start increasing the price?
- Is the meta-data cleaned up? 
  - Is the BOM scrubbed for proper info?  
  - Is extraneous info removed?
- Is the schematic cleaned up?
- Are there traces or planes that can be cleaned up? 
  - e.g. a trace that jumped between layers to get around something, but that something is no longer there
  - In case you put some traces through some planes because you had to, does that perforate the plane too much?
  - Could that be avoided or mitigated somehow?
- Are there stray antenna-like features to the copper?  
  - e.g. Planes that got sliced by a trace and have a connection only on one end


Special thanks to https://github.com/AlpenglowIndustries, https://github.com/jasoncoon, https://github.com/sethkaz, https://github.com/freemovers, https://github.com/SeanMollet, for their invaluable help in this guide.

Have some tips to share? Let me know!

Remember that you are loved. #MakeKindnessNormal
