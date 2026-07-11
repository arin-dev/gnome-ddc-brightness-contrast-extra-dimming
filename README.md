## Set Monitor DDC Brightness/Contrast + Extra Dimming

> [!IMPORTANT]
> **This is a fork with a GNOME 46+ fix.** On GNOME 46 and newer, the original extension breaks dragging windows between workspaces in the Activities overview (`TypeError: Main.uiGroup.remove_actor is not a function` — see [upstream issue #9](https://github.com/tzawezin/gnome-ddc-brightness-contrast-extra-dimming/issues/9) and [fix PR #8](https://github.com/tzawezin/gnome-ddc-brightness-contrast-extra-dimming/pull/8)).
> Until the fix is merged upstream, install from **this repository** (see [installation steps](#install-this-gnome-extension-fixed-version) below) instead of extensions.gnome.org.
> All credit for the extension itself goes to [@tzawezin](https://github.com/tzawezin).

![screenshot](screenshot.png)

### Installation and Configuration

#### Install ddcutil
```
sudo apt install ddcutil
```

#### Make sure i2c-dev is loaded
After installing ddcutil, make sure i2c-dev is loaded:
```
sudo modprobe i2c-dev
```
or add i2c-dev to the /etc/modules file.  
(More info: https://www.ddcutil.com/config_steps/)

#### Add your user to group i2c
```
sudo usermod -aG i2c $USER
```
(More info: https://www.ddcutil.com/i2c_permissions_using_group_i2c/)

#### You can check if its working by trying:
```
ddcutil detect
```

#### More info:
https://www.ddcutil.com/install_config_main/

#### Install this GNOME extension (fixed version)
```
git clone https://github.com/arin-dev/gnome-ddc-brightness-contrast-extra-dimming.git
cd gnome-ddc-brightness-contrast-extra-dimming
rm -rf ~/.local/share/gnome-shell/extensions/ddc-brightness-contrast-extra-dimming@tzawezin.github.io
cp -r "ddc-brightness-contrast-extra-dimming@tzawezin.github.io" ~/.local/share/gnome-shell/extensions/
```
The `rm` line removes any copy previously installed from [extensions.gnome.org](https://extensions.gnome.org/extension/6985/set-monitor-ddc-brightnesscontrast-extra-dimming/) — it uses the same UUID. If the Extensions app later offers you an update for this extension, it will overwrite this patched copy with the (still broken) upstream version, so only accept it once the fix has been merged.

#### Log out / Log in
Log out and back in so GNOME Shell picks up the extension (on X11 you can instead press Alt+F2, type `r`, Enter). Then enable it:
```
gnome-extensions enable ddc-brightness-contrast-extra-dimming@tzawezin.github.io
```
(Also possible from your Extension Manager.)
