# osoyoo-dsi-display-panel
This repository contains a small piece of kernel source which I modified on RK3288 Tinkerboard-S to get my Raspberry PI compatible display panel OSOYOO 7" inch 800x480 working.

# drivers/gpu/drm/bridge/
contains the Toshiba TC358762 DSI/DP display bridge driver which originaly picked up from Tinker OS and a bit modified to not over drive my display pannel.
That means the backlight is limited. This source is ongoing process for now, because I think that the backlight controller part which uses the IC2 should also in this driver encapsulated.

# drivers/input/touchscreen/
contains the Focal FT5406 tochscrenn controller driver 'edt-ft5x06' which originaly picked up from mainline kernel and a bit modified so that the IRQ is an primary option. If IRQ is unsupported on the SBC it will be change into polling mode. In polling mode, the driver will NOT spam you system log :)

# drivers/misc/rockpi/
contains the I2C backlight controller from Radxa RockPI4x kernel 4.4.x. The same uses in the TinkerOS for Tinkerboard(-S). As I mentioned above, this driver is more than fluid - so superfluous. That the functionality simply belongs in the DRM driver. Other device driver manufacturers should also consider this. Because the most beautiful display panel is useless without backlighting.
