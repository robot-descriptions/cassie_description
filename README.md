# Cassie Description

<img src="https://user-images.githubusercontent.com/1189580/197808850-ed5c3be9-aea7-49eb-b7f8-f8e4514c53aa.png" align="right" width=300>

URDF description for Cassie, a biped robot manufactured by Agility Robotics.

This repository is a fork from [jpreher/cassie\_description](https://github.com/jpreher/cassie_description) focussing on the URDF description itself. Head over to the original repository for additional MATLAB and C++ model files. Remember to [cite](#related-literature) the original authors if you are using this description in your academic work.

## Model and URDF Assumptions

Because URDF does not allow for closed-chain kinematics, the pushrod connection ball joints and linkages cannot be represented as a loop in the file. In addition, the URDF is parsed directly into expressions for kinematics and dynamics, so it is not desireable to add these additional coordinates into the system states. The compromise that was made was to include the heel spring as its own linkage, and group the mass properties of the rest of the removed links into the existing ones via parallel axis theorem. This gives us 22 unconstrained degrees of freedom, and a holonomic constraint between the end of the heel spring and the connector on the hip pitch is added into our locomotion model, which enforces the multibar linkage.

Specifically, links which were "removed" and had their mass grouped into others were:

- Knee spring, grouped with the knee assuming an undeflected configuration
- Achilles rod, grouped with the shin assuming a parallel configuration
- Toe output crank and plantar rod, grouped with tarsus assuming the plantar rod is parallel to the tarsus

There is a somewhat rough relationship given between the knee and tarsus angles if the knee and heel springs are undeflected (tarsus = 13deg - knee) that is used by others in their controllers/models/optimizations, but this was not as exact as we desired for explicitly considering the compliance in our model and feedback controller.

## Related Literature

The models used herein are based on the results presented in our ECC publication, and drawn from the existing files and specifications from Agility Robotics.
* Reher, Jenna, Wen-Loong Ma, and Aaron D. Ames. "Dynamic walking with compliance on a cassie bipedal robot." 2019 18th European Control Conference (ECC). IEEE, 2019.
```
@inproceedings{reher2019dynamic,
  title={Dynamic walking with compliance on a {Cassie} bipedal robot},
  author={Reher, Jenna and Ma, Wen-Loong and Ames, Aaron D},
  booktitle={2019 18th European Control Conference (ECC)},
  pages={2589--2595},
  year={2019},
  organization={IEEE}
}
```

* The official Agility Robotics documentation and software release for the Cassie biped.

https://github.com/agilityrobotics/agility-cassie-doc
