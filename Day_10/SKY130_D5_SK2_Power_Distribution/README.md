# SKY130_D5_SK2 – Power Distribution

## Overview

This section covers the Power Distribution Network (PDN) used to distribute power and ground throughout the physical design.

The practical work was performed using the `picorv32a` design with OpenLane/OpenROAD and SKY130.

---

## 1. Power Distribution Network

A Power Distribution Network provides power and ground connectivity throughout the physical design.

The PDN includes structures such as:

- Standard-cell power rails
- Power straps
- Power rings
- Macro power connections
- VDD and GND connections

![Power Distribution Network](images/power_distribution_network.png)

---

## 2. PDN Generation

The PDN stage was executed for the `picorv32a` design using the SKY130 PDN configuration.

The OpenROAD PDN generator reached standard-cell grid insertion and database writing:

```text
[INFO] [PDNG-0013] Inserting stdcell grid - grid
[INFO] [PDNG-0015] Writing to database
```

The PDN configuration included standard-cell rails and metal straps.

---

## 3. PDN Generation Error

During database export, the original OpenROAD PDN flow encountered:

```text
invalid command name "NULL"
```

The detailed call sequence showed:

```text
export_opendb_power_pin
        ↓
$bterm setSpecial
        ↓
NULL setSpecial
```

The flow finally reported:

```text
[CRIT] [PDNG-9999] Unexpected error: invalid command name "NULL"
```

![PDN Generation Error](images/pdn_generation_error.png)

---

## 4. OpenLane Flow Failure

OpenLane subsequently reported that the OpenROAD PDN process exited abnormally:

```text
[ERROR] Exit code: 1
[ERROR] child process exited abnormally
[ERROR] Flow Failed.
```

![PDN Flow Failure](images/pdn_flow_failure.png)

---

## 5. Root-Cause Investigation

The failure was investigated at the OpenDB level.

The investigation showed that the `VPWR` and `VGND` BTerms already existed in the database. The BTerm creation path could therefore return `NULL` when attempting to create an already-existing BTerm.

A source-level modification was developed to reuse an existing BTerm and create a new BTerm only when one does not exist:

```tcl
set net [$block findNet $net_name]
set bterm [$block findBTerm $net_name]

if {$bterm == "NULL"} {
    set bterm [odb::dbBTerm_create $net "${net_name}"]
}

$bterm setSpecial
$bterm setSigType $signal_type
$bterm setIoType "INOUT"
```

A patched OpenROAD binary was successfully built from the same OpenROAD commit used by OpenLane v0.21.

> **Note:** The original PDN execution is documented as a failure/debugging result. It is not presented as a successfully completed PDN stage.

---

## Key Learning Outcomes

- Understanding the purpose of a Power Distribution Network.
- Understanding standard-cell power rails and metal straps.
- Understanding PDN generation in OpenROAD.
- Understanding the relationship between PDN generation and the physical-design database.
- Debugging an OpenDB BTerm-related PDN failure.
- Understanding how a source-level change can address duplicate BTerm handling.

---

## Tools Used

| Tool / Technology | Purpose |
|---|---|
| OpenLane v0.21 | ASIC physical-design flow |
| OpenROAD 0.9.0 | PDN generation |
| OpenDB | Physical-design database |
| SKY130 | 130 nm open-source technology |
| picorv32a | Practical design |
