# AppArmor profiles
AppArmor profiles used on Xubuntu 20.04.

Full system policy is hard to create and maintain. So, the security principle of my AppArmor policy is to create and maintain AppArmor profiles only for programs that communicate with Internet (broswers, email client, ...) or will parse files downloaded from Internet (image viewer, PDF reader, ...).

## Firefox profile
Version tested : 114.0.2

Firefox has internal security mechanisms to isolate its tabs in different namespaces and chroot its child processes. Current Firefox AppArmor profiles in the wild prenvents Firefox to use these security mechanisms.

This AppArmor profile for Firefox enables it to create sandboxed child processes for its tabs.

This profile restrict Firefox from executing external applications (like a PDF viewer for downloaded files for example) and allow download/upload of files only from `$HOME/Public/Firefox/` directory.

## Thunderbird profile
Version tested : 91.3.2

Thunderbird is installed from the tar.gz in a custom location specified by the `@{EXECUTABLE_DIR}` variable.

This profile restrict Thunderbird from executing external applications (like a PDF viewer for downloaded attachments for example) and allow download/upload of attachments only from `$HOME/Public/Thunderbird/` directory.

This profile doesn't allow to use the embded update system of Thunderbird, you have to execute Thunderbird unconfined to use the embded update system with `aa-exec -p unconfined $thunderbird_bin`.

## Signal-desktop profile
Version tested : 5.24.0

This profile allow download/upload of attachments only from `$HOME/Public/Signal/` directory.

## KeepassXC-proxy profile
This profile confine KeepassXC-proxy application for broswer integration with Firefox for the moment.

## Chromium profile
Unmaintened because Xubuntu 20.04 use Snap for Chromium, so I don't use it anymore...

This profile allow download/upload of files only from `$HOME/Public/Chromium/` directory.

## Drive profile
https://github.com/odeke-em/drive version 0.3.9.1

