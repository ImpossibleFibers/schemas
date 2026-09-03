# Background1

This is a schema describing microfluidic flow test videos of microfluidic flow devices developed by Impossible Fibers. Used for microfluidic test videos deposited in [Impossible Fibers' Zenodo](https://zenodo.org/communities/if/records?q=&l=list&p=1&s=10&sort=newest).

| Column | Type | Description |
|---|---|---|
| `filename` | string | Video filename that follows the naming convention: `{flow_device_name}_{fluid1}-{rate1}{unit}_{fluid2}-{rate2}{unit}_{fluid3}-{rate3}{unit}_{formed}[_seq].ext`|
| `droplet_formed` | boolean | Whether a droplet formed during the video run. Classified via visual observation. One of `TRUE`, `FALSE`, or `na`. If the value is `na`, this means either that the flow device is not a droplet generator, i.e. `flow_device_name` is one of [`desalter`] or that there were no droplet generating flow. This is characterize by visual observation of the video run and is prone to subjectivity. |
| `droplet_merged` | int | Whether droplets merged during the video run. One of `0`, `1`, `2`, or `na`. `0 == False`, `1 == True`, `2 == unclear`. This is characterize by visual observation of the video run and is prone to subjectivity. |
| `flow_device_name` | string | Name of the flow device used, corresponds to `flow_device_name` value in `flow_device` schema. |
| `observation` | string | Free-text notes on what was observed during the run. |
| `fluid_1_name` | string | Name/description of the fluid run through channel 1, or `na` if that channel was not used in this run. |
| `fluid_1_rate_value` | int | Flow rate for `fluid_1_name`. `0` if the channel exists on the device but no fluid was flowed through it in this run; `na` only when `fluid_1_name` is also `na`. |
| `fluid_1_rate_unit` | string | Flow rate unit for `fluid_1_rate_value`. Must be a term in the QUDT Unit ontology or `na` if `fluid_1_name` is `na`. |
| `fluid_2_name` | string | Same as `fluid_1_name`, for channel 2. |
| `fluid_2_rate_value` | int | Same as `fluid_1_rate_value`, for channel 2. |
| `fluid_2_rate_unit` | string | Same as `fluid_1_rate_unit`, for channel 2. |
| `fluid_3_name` | string | Same as `fluid_1_name`, for channel 3. |
| `fluid_3_rate_value` | int | Same as `fluid_1_rate_value`, for channel 3. |
| `fluid_3_rate_unit` | string | Same as `fluid_1_rate_unit`, for channel 3. |

## Channels vs. fluids

The `fluid_1_*`, `fluid_2_*`, `fluid_3_*` column groups correspond to a
device's input channels, not to fluids that are necessarily flowing. A
device can have more channels than fluids actually running in a given test —
in that case the unused channel's `fluid_N_name` is still recorded (it's a
real channel on the device) but its `fluid_N_rate_value` is `0` rather than
`na`. `na` across all three columns of a group means that channel is not
present/applicable for this row at all, whereas a rate of `0` means the
channel exists but had no fluid flowing through it during that run.