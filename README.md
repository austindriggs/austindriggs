# PHOTOVOLTAICS

## OVERVIEW

### WHAT IS IT?

The term "photovoltaic" combines "photo," meaning light, and "voltaic," referring to electricity. These devices directly convert sunlight into electricity through the photovoltaic effect. The photovoltaic effect was first observed by Alexandre-Edmond Becquerel in 1839, and the technology has evolved significantly since then.

In essence, a photovoltaic system comprises solar cells that generate electrical power when exposed to sunlight. These cells are typically made of semiconductor materials, such as (doped) silicon, which release electrons when illuminated, creating an electric current.

### WHY DO WE USE IT

Photovoltaics find extensive use in both commercial and residential settings due to their environmentally friendly and sustainable nature. In commercial applications, businesses leverage solar power to:

- Reduce energy costs
- Enhance corporate social responsibility
- Contribute to a cleaner environment

Residentially, photovoltaic systems offer homeowners the opportunity to generate their electricity, leading to reduced reliance on conventional grid power. The engineering behind photovoltaics focuses on optimizing solar cell efficiency, durability, and cost-effectiveness. By harnessing the power of sunlight, photovoltaics contribute to a more sustainable and renewable energy future.

## SYSTEM ARCHITECTURE DIAGRAM

![big-picture](https://www.literoflightusa.org/wp-content/uploads/2021/03/solar-panel-wiring-diagrams.png)

### OHMS LAW

Before we get into it, lets start simple. At this level, Ohm's law _should_ always be true:

`V = I x R`

This should solve literally any voltage or current calculations throughout the system design. If not please correct me.

### SOLAR CELLS

TODO

### JUNCTION BOX

- Purpose: The junction box is a component integrated directly into individual solar panels. Its main function is to protect the electrical connections within the solar panel. The junction box houses diodes that prevent reverse current flow, ensuring that the generated power moves in the intended direction.
- Connection: Junction boxes are part of each solar panel, managing the internal wiring and connections specific to that panel. They are typically mounted on the backside of the panel.

### COMBINER BOX

- Purpose: The combiner box serves as a central consolidation point for the DC outputs of multiple solar panels. Its primary purpose is to streamline the individual electrical outputs from these panels before sending the combined power to the inverter. By combining the outputs in parallel, the combiner box maximizes the overall power output of the solar array.
- Connection: Combiner boxes are strategically placed between the solar panels and the inverter. They have multiple input terminals, each connected to a solar panel, allowing for the parallel connection of these panels.

**SOURCE**: [ATO PV Combiner Box vs. Junction Box](https://www.ato.com/pv-combiner-box-vs-junction-box)

### INVERTER

A solar power inverter converts or inverts the direct current (DC) energy produced by a solar panel into Alternate Current (AC.)

Most homes use AC rather than DC energy. DC energy is not safe to use in homes. If you run Direct Current (DC) directly to the house, most gadgets plugged in would smoke and potentially catch fire. The result would be that most appliances, computers, power strips, TVs, entertainment systems, home security devices, and a whole host of other electronics would become fried. Solar arrays use inverters to change the DC to AC, which is safe for home usage.

**SOURCE**: [A Guide to Solar Inverters](https://solarmagazine.com/solar-inverters/)

### STRING INVERTER

- Panels are connected in **series**. This means that one current flows through the entire circuit, and the current is limited by the lowest current-producing panel. 
- This application is best when all panels face _generally_ in the same direction and are all expected to produce the same amount of power.

![series](https://www.allaboutcircuits.com/uploads/articles/Figure_2._Series_circuit_.jpg)

### MICROINVERTER

- Panels connected in **parallel**. This means that each panel can have its own current flowing through it and the current through each is independent of any other panel in the circuit. 
- This application is best when panels are expected to receive different amounts of sunlight. This could occur when:
    - Panels face different directions
    - Shading from trees
    - Shading from chimneys

![parallel](https://www.allaboutcircuits.com/uploads/articles/Figure_3._Parallel_connection_of_resistors__.jpg)

**QUESTION**: What happens if you have marginal shading? Probably go with the string inverter because it is cheaper. This is when the engineer steps in to decide what the best outcome is.

**SOURCE**: [Micro Inverters vs String Inverters](https://youtu.be/eekosGR8XHQ?si=cpK52wKvy9UfdTtg) by Electrum

![differences](https://www.solarreviews.com/content/images/blog/c40833-SR_String&MicroInverters3.jpg)

### OPTIMIZER

- Purpose: Power optimizers are a relatively new technology in the solar industry and can be considered a compromise between a microinverter and a string inverter (though it IS NOT either one). It tracks the maximum power of each panel in real time and smooths out the electricity generated before sending it to the inverter. This smoothing out (reduction of pulses) allows the **string** inverter to process much more electricity.
- Connection: It is installed on individual solar panels

![average-power](https://rahsoft.com/wp-content/uploads/2021/04/Screenshot-2021-05-07-at-13.18.39.png)

This picture DOES NOT relate to photovoltaics, but is how I'd imagine an optimizer works (at an extremely low level, do your own research). The blue is the input to the optimizer, and the red is the output from the optimizer. 

### CHARGE CONTROLLER

At a very low level, the charge controller should do the same thing. It "smooths" out the charging of the battery in order to prevent spikes in current flow: at a higher level it regulates the power flow between the solar panel and the battery, ensuring that the battery remains at a consistent state of charge.

**QUESTION**: How does it do this? The solar charge controller works by measuring the voltage of the batteries and the solar panels and adjusting the flow of electricity accordingly. When the batteries are fully charged, the controller will reduce the amount of electricity flowing into the batteries to prevent overcharging. On the other hand, if the batteries have a low charge, the controller will increase the flow of electricity to recharge them. 

SUMMARY: Battery has low charge, controller sends lots of power. Battery has high charge, controller sends little power.

### PULSE WIDTH MODULATION (PWM)

- PWM is one of the most basic signal that you can send. This is why its generally used for smaller, simpler designs, in both photovoltaics and general electrical engineering.
- If you've even taken a video or slomo of a car or something else with LEDs in it you've seen PWM. Notice how the LEDs are turning on and off very quickly? That's the PULSE. When you use WIDTH MODULATION in it, you change the duration (percentage, usually called the duty cycle) of the pulse. 

![pwm](https://circuitdigest.com/sites/default/files/projectimage_tut/Pulse-Width-Modulation.jpg)

**QUESTION**: Why is this useful? I'm not sure what its used for in the charge controller but I'd say its useful for "efficiency" (which is a very broad term), because that's why its used for LEDs (and dimming them: the lower the duty cycle percentage, the longer the LED is off, and the more it appears "dim" to our human eyes). The other reason PWM can be used is to convert a **digital** signal into an **analog** signal. 

![pwm-to-analog](https://www.kebamerica.com/wp-content/uploads/2020/02/pwm-for-different-output-frequencies-300x245.png)

### ELECTRICITY PHASES

This (should) be the only spot with videos. Yes they are long, YES they are useful. Please watch them.

[How ELECTRICITY works - working principle](https://youtu.be/mc979OhitAg?si=OrNGf4Ug5FURv6v2) by The Engineering Mindset
Summary: Skip to `3:59 - Current` and watch the rest of the video.

[How Three Phase Electricity works - The basics explained](https://youtu.be/4oRT7PoXSS0?si=ecwPp0NKLMvAaH6J) by The Engineering Mindset
Summary: How and why we use 1, 2, and 3 phases (and not 4, 5, or 6).

These videos are FUNDAMENTAL to electrical engineering (you'll learn more in AC Analysis) and are worth the watch.

**QUESTION**: Why do we use AC for electricity? It is easier to transmit over long distances. Solar panels by design (just by the laws of chemistry and physics) produce DC current, but we want AC. That's what the inverter is for.

### MC CONNECTORS

- Not sure on the question here, these are just the connector they use I guess.
- MC connectors are specially designed for low contact resistance and good stable connections under a wide range of conditions. MC means "multi-contact." The term "multi-contact" comes from the fact that the connectors have a bunch of little spring loaded gold plated fingers that ensure good contact.The first company to manufacture them is also named Multi-Contact, but Tyco connectors are used on some modules.
- So what do they do for me?
    - Commonly referred to as MC cables or MC connectors, these have started to take over much of the wiring of solar arrays. Nearly all major manufacturers now supply panels only with MC connectors, or as an option to the standard junction box with screw type terminals. All current production solar panels made for grid-tie applications now come only with MC connectors.
    - Simplified wiring, especially for medium and larger arrays, makes series and parallel wiring of panels much easier. Long series connections often needed for high voltage grid tie systems are "plug and play."

**SOURCE**: [What are MC Connectors and Cables?](https://www.solar-electric.com/learning-center/what-are-mc-cables-connectors.html/)

### STRING SIZE CALCULATIONS

PLEASE ask as many questions as you can about how to design a system. You can always look stuff up later, but the general design is the big idea of this class (and I think a big part of the test but I don't remember). I remember doing a full design on somebody's house in the class and it was extremely helpful to run through the entire design process on the last day of class. I might fill this section in later but don't have time right now.

Some sources that looked good:
- [Calculating Solar PV String Size – A Step-By-Step Guide](https://solardesignguide.com/calculating-string-size/)
- [How-To Determing Solar String Size (Examples + Calculator)](https://solarplansets.com/learn/how-to-determing-solar-string-size/)
- [String Sizing Guide: How Many Solar Panels Can I String Into My Inverter?](https://unboundsolar.com/blog/string-sizing-guide)

### BALANCE OF SYSTEMS

I didn't learn about this when I was in the class. Looks to be just making sure that your system is the most efficent it can be for the least amount of cost: Balancing efficency compared to cost.

Some sources that looked good (again just don't have time for this larger idea/topic):
- [Balance of Solar PV Systems (BOS)](https://www.greentechrenewables.com/article/balance-solar-pv-systems-bos)
- [Understanding Solar Panel Balance of System (BOS)](https://us.solarpanelsnetwork.com/blog/solar-panel-balance-of-system-bos/)

## ADDITIONAL RESOURCES

- TODO
