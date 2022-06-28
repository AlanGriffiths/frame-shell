# Frame Shell

Frame Shell is a small example of using Ubuntu Frame to provide a single
app user session. It comprises two files:

File | Description
--|--
frame-shell | This is a script that runs an application using Ubuntu Frame
frame-shell.desktop | This is a desktop entry for the greeter that invokes frame-shell

These files need to be copied to `/usr/bin` and `/usr/share/wayland-sessions` respectively.

## Prerequisites

The files as supplied are set up to use `mir-kiosk-neverputt` as the app.

1. Ubuntu Frame must be installed: `snap install ubuntu-frame`
2. The application to use must be installed. E.g.: `snap install mir-kiosk-neverputt`

## Setup

If you wish to use a different application, edit `frame-shell.desktop` "Exec"
line to contain your chosen application.

Ensure that both are configured with all plugs connected:

```
/snap/ubuntu-frame/current/bin/setup.sh
/snap/mir-kiosk-neverputt/current/bin/setup.sh
```

Also, neverputt uses some additional Wayland extensions we need to enable in
Ubuntu Frame:

```
snap set ubuntu-frame config="
add-wayland-extensions=zwp_pointer_constraints_v1:zwp_relative_pointer_manager_v1"
```

Now copy the files where they are needed:

```
sudo cp frame-shell /usr/bin/
sudo cp frame-shell.desktop /usr/share/wayland-sessions/
```

## Use

Now logout and log in again selecting "Frame neverputt" from the login screen.
