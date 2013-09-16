# Cell-Transmission Model on MATLAB

Implementation of Cell-Transmission Model in platform of MATLAB

### type of cell, link and lane
> Date: August 23rd, 2013

type | cell   | lane   | link
-----|--------|--------|----------
0    | normal | normal | straight
1    | input  | input  | merge
2    | output | output | diverge

### construction of the model
> Date: August 22nd, 2013

The model variables are put into the global workspace. The lists of cells and links are the fundamental elements of the model. But, the cells and links are not created directly for avoiding the complexity. Instead, the lists of lanes and intersections are constructed, and when a lane or an intersection is added, the correspondent cells and links are added into the model.

In detail, the construction of the model consists of the following functions:

    reset_ctm()
    ctm_add_lane(t,cap,sat_rate,in_rate,out_rate)
    ctm_add_int(in_lanes,out_lanes,cells)
    ctm_add_phase(index,links)

### simulation
> Date: August 23rd, 2013

Every step of the simulation consists of three steps:

1. calculate the possible in/out flows (based on cell settings)
2. calculate the real flows (based on link settings)
3. update the lengths of cells

Furthermore, during the simulation, some parameters should be able to be modified, such as the phases of intersections (+1) and the rates of lanes.

### read results
> Date: August 23rd, 2013

The simulation result should be able to be appropriately read. In detail, the following reading functions should be defined.

    c_lens = ctm_read_cells()
    queues = ctm_read_lanes()
    phases = ctm_read_phases()

