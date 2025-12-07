---
layout: project
title: Torque Wrench Design
description: 600 in-lbf Torque Wrench Design Project for Mechanics of Engineering Materials
technologies: [MATLAB, Autodesk Fusion, ANSYS]
image: /assets/images/displacement.png
---

I designed a simplified 600 in-lbf torque wrench with the following requirements: 
- A safety factor against yield of 4
- A safety factor for crack growth from an assumed crack of depth 0.04 in of 2
- A fatigue stress safety factor of 1.5
- A minimum strain gauge of 1 mV/V

Using MATLAB, I iterated over different width and thickness values to meet the requirements. As shown in the following image, I selected a thickness of 0.4 inches and a width of 0.7 inches. The length of the wrench was left at the baseline design of 16 inches, which allows for a reasonable required input force of 37.5 pounds. The strain gauge is located an inch from the drive. The dimensions of the drive were set, and to reduce stress concentrations a fillet of 0.5 in was applied.

![Image of CAD model]({{ "/assets/images/CADdimensions.png" | relative_url }}){: style="width: 800px; display: block; margin: 0 auto;" }

I selected Ti-6Al-4V (aged) as the material for the torque wrench due to its favorable balance of strength, toughness, and fatigue resistance. Key material properties are:
- Young's Modulus = 16.1e6 psi
- Poisson's Ratio = 0.36
- Tensile Strength = 148 ksi
- Plane Strain Fracture Toughness (Kic) = 74.6 ksi-in^0.5
- Fatigue Strength = 87.4 ksi

Ti-6Al-4V has a high yield strength and moderate fracture toughness relative to its Young's Modulus, unlike other high-strength alloys such as tool steels. This combination illustrates that Ti-6Al-4V maintains strength without becoming overly brittle under torsional loading. Furthermore, Ti-6Al-4V exhibits excellent fatigue strength, especially compared to aluminum alloys, making it well-suited for a torque wrench that must withstand repeated loads.

Using these selected material and geometric properties, I created a CAD model in Autodesk Fusion and then used ANSYS to model the deformation, stresses, and strains of the wrench under its maximum torque of 600 in-lbf. I clamped the drive 0.1 inches above the wrench, and applied a load of 37.5 lbs in the positive x direction.

![Applied load and boundary conditions]({{ "/assets/images/BCs.png" | relative_url }}){: style="width: 800px; display: block; margin: 0 auto;" }

ANSYS produced the following results:
![Normal strain contours]({{ "normalstraincontours.png" | relative_url }}){: style="width: 800px; display: block; margin: 0 auto;" }

![Maximum principal stress contours]({{ "maxprinstress.png" | relative_url }}){: style="width: 800px; display: block; margin: 0 auto;" }

![Maximum principal stress, zoomed]({{ "maxprinstresszoom.png" | relative_url }}){: style="width: 800px; display: block; margin: 0 auto;" }

![Normal stress contours]({{ "normstresszoom.png" | relative_url }}){: style="width: 800px; display: block; margin: 0 auto;" }

ANSYS calculated a maximum normal stress of 67243 psi. Since this occurs where the clamped boundary condition ends, it is a mathematical stress singularity and likely not a realistic maximum. A more realistic value occurs as a stress concentration between the drive and beam.

![Maximum stress, neglecting singularity]({{ "truemax.png" | relative_url }}){: style="width: 200px; display: block; margin: 0 auto;" }

This indicates the maximum is 53984 psi, which is 98% higher than the calculated maximum stress of 18370 psi using beam theory. This is expected as the model does not account for stress concentrations. Using this true maximum, the torque wrench has a safety factor for strength of 2.7, which is lower than the ideal of 8.1 and too low to meet the requirement. The fatigue stress safety factor and crack growth safety factor are 1.62 and 3.48, respectively, which meet requirements but are lower than the theoretical values of 4.76 and 10.23. While I did not reiterate my design to account for this stress concentration, in practice it would be critical to either reduce stress concentrations through filleting or handle them with a stronger material. Notably, beam theory is highly accurate away from the clamped drive; at the gauge section, the expected stress was 17,219 psi, and ANSYS predicted 17,220 psi, showing nearly zero error.

ANSYS determined the maximum load point deflection to be 0.37016 inches.
![Wrench displacement]({{ "displacement.png" | relative_url }}){: style="width: 800px; display: block; margin: 0 auto;" }
This is 28.4% higher than the calculated maximum deflection of 0.278 inches, using beam theory. The discrepancy is likely primarily due to partially clamping the drive, leading to some rotation in the drive as well.

At the strain gauge, ANSYS outputs a strain of 1069.6 microstrain, which has essentially zero error with the predicted value of 1069.53 microstrain. Using the ANSYS strain value and assuming a half-bridge strain with a gauge calibration factor of 2, the torque wrench sensitivity equals 1.0696 mV/V. This meets the design requirement. 

Selected strain gauge:
350 Ω half-bridge Model No. SGT-1LH/350-TY11 by DywerOmega with a carrier length of 0.563 and height of 0.157 would fit on the wrench and be easy to install.