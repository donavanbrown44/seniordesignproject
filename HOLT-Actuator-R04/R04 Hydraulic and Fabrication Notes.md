# HOLT actuator R04

Open `HOLT Installed R04 - 14 mm valve.SLDASM` for valve 3-14038-01, or select one of the three valve configurations in `HOLT Installed R04 - 11 mm valves.SLDASM`. Keep `R04 Parts` and `HOLT References` next to the assemblies. The installed assemblies use SolidWorks 2026 native files.

## SolidWorks checks

`Travel Check.csv` records 37 actuator-only poses from 0° to 90° with zero solid overlaps. `Installed Travel Check.csv` records seven poses on each of the four HOLT valve bodies with zero unexpected overlaps. The supplied single-body valve models have fixed stems. For intermediate angles, the installed check excludes only the contact between that static stem and its rotating drive insert. Both end poses check the full geometry. The reference pose is the supplied valve pose with the actuator rods near extension. Confirm which command opens the installed valve during commissioning.

`HOLT Installed R04 - 14 mm live motion.SLDASM` adds native rack-and-pinion mates and a 43.197 mm rack travel limit. SolidWorks verified the 14 moving components at 0°, 45° and 90°. The file reopens at 90° with the cover and upper bearing parts hidden for access. To move it, select the upper rack, choose **Move Component → By Delta XYZ**, and apply `5mm` in ΔX. The supplied HOLT valve reference is a single solid. The motion model drives the pinion and insert while using that fixed valve reference.

`HOLT Installed R04 - 14 mm live valve.SLDASM` also moves the butterfly disc. It uses a housing-only copy of HOLT 3-14038-01 and a reconstructed disc and stem based on that part’s features. The drive insert and rotor are locked together. A separate SolidWorks verification copy cycled from 90° through 45° to closed and back, with zero solid overlaps at each sampled pose. The live valve assembly starts closed. Select rack instance `<1>` and apply `-5mm` in ΔX under **Move Component → By Delta XYZ** to start opening the valve.

Bench torque, component strength, final fastener details and the physical truck hose route still need verification before hardware release.

## Mechanism

- Two SMC CHQB32-50D cylinders with 32 mm bores, 50 mm strokes, 16 mm rods and M10 × 1.5 female rod ends. The catalog calls out a 115 mm body length, a 34 mm square mount pattern, and four CQ-M5×115L mounting bolts per cylinder. Keep the port flats accessible for hose installation. [SMC catalog, dimensions and mounting](https://ca01.smcworld.com/catalog/iFilter-Hyd-en/mpv/E112-HYD-CHQ/data/E112-HYD-CHQ.pdf)
- Module 2.5, 20° pressure angle, 22-tooth pinion, 55 mm pitch diameter. A 90° turn requires 43.20 mm rack travel. Centering the rack travel in each nominal 50 mm stroke leaves about 3.40 mm at each end. Adjust the frame stops with the valve connected and verify seating and piston reserve together.
- For the gear quote, count two identical 152 mm overall, 17-tooth rack bars with 15.2 mm faces and one 60 mm nominal OD pinion with a 16 mm face, 31 mm and 24 mm journals, and a socket for the interchangeable insert. Have the gear shop generate the cutter profile from module and pressure angle. Set material, tooth hardness, root shape, backlash and tolerances from the validated load case before machining.
- Use the rack reaction strips and guided crossheads to carry mesh and bridge reactions into the common base. The rod studs have radial clearance through the crossheads and captive thrust faces. Establish the final lateral clearance and axial endplay on the finished assembly. Oil and grease belong on their respective sides of the rod gland.
- For a low-cost base, use flat steel blanks for the flange, continuous plate and bearing register, then finish the mounting faces, guide references and bearing bores once the stack is joined. The SolidWorks base solid represents the resulting geometry. Set the joining method, flatness and fastener sizes with the shop. Use a bent 5052 cover for splash protection, with access and drainage for the actual installation.
- The package is 212 × 192 × 87.6 mm at the cover and approximately 95 mm tall at the elbows, excluding the valve and hoses. Cylinder axes are 138 mm apart. Each rod axis is 41.5 mm from its rack pitch line. Check the mounting-foot fasteners and guide stiffness for the offset load. Check the stops for the full force of both cylinders if one stop takes load first.

## Truck hydraulic interface

```text
Regulated hydraulic supply -> directional valve P
Directional valve T        -> low-backpressure tank return

Directional valve A        -> tee -> cylinder 1 cap end
                                 -> cylinder 2 cap end
Directional valve B        -> tee -> cylinder 1 rod end
                                 -> cylinder 2 rod end
```

The cylinders face opposite directions, so both rods extend together and both rods retract together. Use A to extend and B to retract. Verify which command corresponds to open on each installed valve before labeling it. Mount the A/B tees on the truck or a fixed bracket, support each branch, and verify hose bend radius and chafe clearance against the physical truck. The candidate hose lengths in the BOM are for pricing and require a tape-measured route.

Using 100 psi supply at the cylinders and negligible return pressure, ideal output is approximately 30.5 N·m extending and 22.9 N·m retracting. With the provisional 75% efficiency and 1.5× sizing margin, the weaker direction supports about 11.4 N·m measured valve torque at 100 psi or 9.1 N·m at 80 psi. Return backpressure and seal drag reduce available output. At 500 psi, ideal extension torque is about 153 N·m and each extending rack sees about 2.77 kN. Set the operating pressure from the verified valve load and the tested mechanical limit. SMC specifies 3.5 MPa maximum and 0.3 MPa minimum operating pressure, plus an ambient and fluid minimum of −10 °C for this configuration. Use a protected hydraulic supply and verify surge and trapped-line pressure control with the truck schematic and measured supply and return pressures. [SMC specifications and output table](https://ca01.smcworld.com/catalog/iFilter-Hyd-en/mpv/E112-HYD-CHQ/data/E112-HYD-CHQ.pdf)

## Cost boundary

The costed BOM uses public unit prices for listed stock, your $100 gear-shop allowance, and explicit allowances for shop stock and consumables. Confirm that the gear scope includes the shaft journals and specified tooth material and finish. The listed price subtotal is $363.16. The provisional cash subtotal is $558.16 before labor, freight, tax, truck installation or new pressure-control hardware. A firm bought-and-built number requires the fabricator's price and confirmation of the truck interfaces.

For a protected bench branch that needs its own regulator, a Sun PRDB-LDN cartridge and EJI three-port body are a $126.35 catalog reference pair before the gauge, plumbing and work-port protection. Confirm suitability, availability and the required pressure range for the actual circuit before selection. [Cartridge listing](https://aheinfo.com/product/sun-prdb-ldn-cart-valve/) · [Body listing](https://www.hydrotech.com/product/sun/EJI)
