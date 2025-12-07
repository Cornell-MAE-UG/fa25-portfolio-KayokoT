---
layout: project
title: Torque Wrench Design
description: 600 in-lbf Torque Wrench Design Project for Mechanics of Engineering Materials
technologies: [MATLAB, Autodesk Fusion, ANSYS]
image: /assets/images/displacement.png
---

I designed a simplified 600 in-lbf torque wrench with the following requirements: 
a. A safety factor against yield of 4
b. A safety factor for crack growth from an assumed crack of depth 0.04 in of 2
c. A fatigue stress safety factor of 1.5
d. A minimum strain gauge of 1 mV/V

Using MATLAB, I iterated over different width and thickness values to meet the requirements. As shown in the following image, I selected a thickness of 0.4 inches and a width of 0.7 inches. The length of the wrench was left at the baseline design of 16 inches, which allows for a reasonable required input force of 37.5 pounds. The strain gauge is located an inch from the drive. The dimensions of the drive were set, and to reduce stress concentrations a fillet of 0.5 in was applied.

![Image of CAD model]({{ "/assets/images/CADdimensions.png" | relative_url }}){: .inline-image-r style="width: 200px"}

I selected Ti-6Al-4V (aged) as the material for the torque wrench due to it's favorable balance of strength, toughness, and fatigue resistance. Key material properties are:
- Young's Modulus (E) = 16.1e6 psi
- Poisson's Ratio = 0.36
- Tensile Strength = 148 ksi
- Plane Strain Fracture Toughness (Kic) = 74.6 ksi-in^0.5
- Fatigue Strength = 87.4 ksi

Ti-6Al-4V has a high yield strength and moderate fracture toughness relative to its Young's Modulus, unlike other high-strength alloys such as tool steels. This combination illustrates that Ti-6Al-4V maintains strength without becoming overly brittle under torsional loading. Furthermore, Ti-6Al-4V exhibits excellent fatigue strength, especially compared to aluminum alloys, making it well-suited for a torque wrench that must withstand repeated loads.

Using these selected material and geometric properties, I created a CAD model in Autodesk Fusion and then used ANSYS to model the deformation, stresses, and strains of the wrench under its maximum torque of 600 in-lbf. I clamped the drive 0.1 inches above the wrench, and applied a load of 37.5 lbs in the positive x direction.

![Applied load and boundary conditions]({{ "/assets/images/BCs.png" | relative_url }}){: .inline-image-r style="width: 200px"}

ANSYS produced the following results:
![Normal strain contours]({{ "normalstraincontours.png" | relative_url }}){: .inline-image-r style="width: 200px"}

<figure style="text-align: center;">
  <div style="display: flex; justify-content: center; gap: 12px;">
    <img src="{{ 'maxprinstress.png' | relative_url }}" style="width: 200px;">
    <img src="{{ 'maxprinstresszoom.png' | relative_url }}" style="width: 200px;">
  </div>
  <figcaption style="margin-top: 6px; font-style: italic;">
    Maximum principal stress contours
  </figcaption>
</figure>

