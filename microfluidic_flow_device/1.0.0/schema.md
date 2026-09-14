# Background

This is a schema describing microfluidic flow devices developed by Impossible Fibers.  Used for flow device metadata deposited in [Impossible Fibers' Zenodo](https://zenodo.org/communities/if/records?q=&l=list&p=1&s=10&sort=newest).

| Column | Type | Description |
|---|---|---|
| `flow_device_name` | string | Human-readable name of the flow device. Unique per row. Corresponds to `flow_device_name` value in flow_device_videos schema.|
| `device_img_filename` | string | Top-down (overhead) photo of the flow device's etched microfluidic channel, taken before fluid flow/testing began. `na` if no such photo was captured for this device.|
| `tape_used` | string | Tape product used to seal the device. Two observed values: `AR 94119`, `3M 850`.  `3M 850` specs can be found [here](https://www.3m.com/3M/en_US/p/d/b40071908/?gad_campaignid=20027834637&gbraid=0AAAAACgp1ZqOLa2xAzP0TZ_PDQbxJNNuu). `AR 94119` specs can be found [here](https://www.adhesivesresearch.com/arseal-94119/)|
| `device_type` | string | Device type. Three observed values: `double encapsulation droplet`, `single encapsulation droplet`, `desalter`. |