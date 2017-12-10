# Vagrant Sublime Text config box

This Vagrantfile will create a new CentOS 7 box, install X11, Openbox, and Sublime Text, and link the config directory to the shared folder. The aim is to make it easy to package up your Sublime config on a clean VM ready for copying to a machine which may not have internet access.

List any packages to install in `sublime-text-3/Packages/User/Package Control.sublime-settings` and they'll be downloaded after enabling and restarting Package Control.

This is a work in progress, isn't ready, and doesn't work yet.
