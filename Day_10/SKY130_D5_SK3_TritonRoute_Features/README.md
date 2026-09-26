# SKY130_D5_SK3 – TritonRoute Features

## Overview

This section covers TritonRoute features used during detailed routing in the physical design flow.

Topics covered include:

- Fast routing and detailed routing
- Route-guide preprocessing
- Panel-based routing
- Connectivity
- Access points
- Routing topology

The practical implementation uses the `picorv32a` design with OpenLane/OpenROAD and SKY130.

---

## 1. Fast Route and Detailed Route

Routing can be viewed as a combination of fast/global routing and detailed routing.

The fast routing stage provides routing information that is subsequently refined during detailed routing.

![Fast and Detail Routing](images/routing_fast_and_detail.png)

---

## 2. Preprocessed Route Guides

Route-guide preprocessing prepares routing information for detailed routing.

The training material covers operations such as:

- Splitting
- Merging
- Bridging
- Generation of preprocessed guides

![Preprocessed Route Guides](images/preprocessed_route_guides.png)

---

## 3. Parallel and Sequential Panel Routing

Panel-based routing divides the routing problem into manageable routing regions.

The routing process can involve:

- Intra-layer parallel routing
- Inter-layer sequential routing
- Routing across multiple metal layers

![Parallel and Sequential Panel Routing](images/parallel_sequential_panel_routing.png)

---

## 4. Connectivity and Access Points

TritonRoute uses access points to establish connectivity between routing objects.

An Access Point (AP) is an on-grid point on a metal layer that can be used to connect routing segments, pins, I/O ports, or other routing layers.

An Access Point Cluster (APC) groups related access points.

![TritonRoute Connectivity and Access Points](images/tritonroute_connectivity_access_points.png)

---

## Practical Routing Connection

The `picorv32a` design was routed using the OpenLane physical-design flow.

The routing run was:

```text
25-09_04-32
```

The routing stage reported:

```text
[INFO]: Routing completed for picorv32a/25-09_04-32
```

The routed design generated:

```text
picorv32a.def
picorv32a.def.png
picorv32a.def.ref
picorv32a.spef
```

This provides a practical connection between the TritonRoute concepts and the routed `picorv32a` implementation.

---

## Key Learning Outcomes

- Understanding the role of TritonRoute in detailed routing.
- Understanding fast and detailed routing.
- Understanding route-guide preprocessing.
- Understanding panel-based routing.
- Understanding access points and access point clusters.
- Understanding routing connectivity.
- Connecting TritonRoute concepts with a practical routed design.

---

## Tools Used

| Tool / Technology | Purpose |
|---|---|
| OpenLane v0.21 | ASIC physical-design flow |
| OpenROAD 0.9.0 | Physical-design implementation |
| TritonRoute | Detailed routing |
| SKY130 | 130 nm open-source technology |
| picorv32a | Practical design |

