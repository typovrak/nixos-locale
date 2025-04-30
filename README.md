# 🗣️ NixOS Locale

> Declarative NixOS module to configure system timezone and comprehensive locale settings with en_US base with French regional formats.

## 📦 Features

- 🌍 **Timezone :** Sets ```time.timeZone = "Europe/Paris"```.

- 🗣️ **Default locale :** Configures ```en_US.UTF-8``` as the system-wide ```defaultLocale```.

- 🇫🇷 **French regional formats :** Applies French settings for address, identification, measurement, monetary, name, numeric, paper size, telephone and time with ```fr_FR.UTF-8```.

- 🔄 **Idempotent :** Safe to import in any NixOS rebuild, always enforces the same locale state.

- ⚙️ **Zero-friction :** No additional options required—just import the module.

## ⚙️ Prerequisites

### 1. NixOS version
Requires NixOS 24.11 or newer.

### 2. User validation
the target user must be defined in ```config.username```. See [typovrak main nixos configuration](https://github.com/typovrak/nixos) for more details.

### 3. Backup
No backup needed for this module.

## 🚀 Installation
Fetch the module directly in your main nixos configuration at ```/etc/nixos/configuration.nix``` using fetchGit
```nix
# /etc/nixos/configuration.nix

let
  nixos-locale = fetchGit {
    url = "https://github.com/typovrak/nixos-locale.git";
    ref = "main";
    rev = "d148a8f975f2a9aa5544c40525d860498e9e5af4"; # update to the desired commit
  };
in
{
  imports = [
    /etc/nixos/hardware-configuration.nix # system hardware settings
    /etc/nixos/variables.nix # defines config.username and other variables, see https://github.com/typovrak/nixos for more details
    (import "${nixos-locale}/configuration.nix")
  ];
}
```

Once imported, rebuild your system to apply changes
```bash
sudo nixos-rebuild switch
```

## 🎬 Usage

Verify localization with
```bash
timedatectl status
```
And
```bash
locale
```

## ❤️ Support

If this module saved you time, please ⭐️ the repo and share feedback.  
You can also support me on ☕ [Buy me a coffee](https://www.buymeacoffee.com/typovrak).

## 📝 License

Distributed under the [MIT license](LICENSE.md).

## 📜 Code of conduct

This project maintains a [code of conduct](.github/CODE_OF_CONDUCT.md) to ensure a respectful, inclusive and constructive community.

## 🛡️ Security

To report vulnerabilities or learn about supported versions and response timelines, please see our [security policy](.github/SECURITY.md).

---

<p align="center"><i>Made with 💜 by typovrak</i></p>
