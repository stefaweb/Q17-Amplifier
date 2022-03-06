To properly run Q17 simulations, several libraries must be included into project.
These are proprietary, but can be downloaded from:
OPA1641 ->https://www.ti.com/lit/zip/sbom627 unzip and extract OPA1641.LIB
FQA36P15 -> https://www.onsemi.com/pub/collateral/fqa36p15.lib
FQA46N15 -> https://www.onsemi.com/pub/collateral/fqa46n15.lib
FQP3N30 -> https://www.onsemi.com/pub/collateral/fqp3n30.lib
FQP3P20 -> https://www.onsemi.com/pub/collateral/fqp3p20.lib
 
Download these and place in the same directory with Q17 ltspice asc file. Open simulation file with ltspice and include following spice directives:
.inc OPA1641.LIB
.inc fqa36p15.lib
.inc fqa46n15.lib
.inc fqp3n30.lib
.inc fqp3p20.lib
 
To run transient, uncomment ;.tran 0 200m 100m 10m
