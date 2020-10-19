# gPodder Server

Base configuration for a new Ubuntu GNU/Linux box.

## Synopsis

Bootstraps a brand new Ubuntu 18.04+ server or desktop with locked down security and highly opinionated defaults.

* Updates all packages the first time the script is run.
* Sets Neovim as the default editor and installs it from the Neovim PPA.
* Sets Byobu to run by default and installs it from the Byobu PPA.
* Installs LibreOffice from the LibreOffice PPA, for desktop machines only.
* Sets the zshell with oh-my-zsh as the default shell.
* Sets up UFW, Fail2Ban, unattended upgrades, and logwatch.
* Disallows all incoming connections except SSH.
* Only allow SSH for managed users using key-based authentication.
* Disallow SSH access for root.
* Manage the machine's hostname.
* Manages the user accounts on the machine.

## Requirements

This role is only maintained for Ubuntu GNU/Linux 18.04 and above.

This role does not rely on any third-party roles.

## Parameters

| Parameters        | Choices/Defaults                    | Comments                                                                                                 |
|-------------------|-------------------------------------|----------------------------------------------------------------------------------------------------------|
| dev               | **Default:**<br>[]                  |                                                                                                          |
| doc               | **Default:**<br>[]                  |                                                                                                          |
| setup             | **Default:**<br>[]                  |                                                                                                          |
| test              | **Default:**<br>[]                  |                                                                                                          |

## Notes

ℹ️ Note
* The upgrade of all packages on the machine only happens on the _first_ run. This is detected by the hostname being not already set to what is provided in the playbook. If the hostname is already pre-configured on the machine then the full package upgrade will not happen. If the hostname is changed the full package upgrade will run again.


## Examples

```yaml
- name: Base configuration
  maxolasersquad.gpodder-server:
    admin_users:
      - name: john
        pubkey: ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCmwlHMPRU7fd3+ucsB221yeB4aaPLLBHaaBKQ4GbVQkkdDNSkMkRNXOg9uJl23UjPW5E9Hu4rl+dfZoU7PiPx05IxZAgaJDrc8dbfEGx5egpM/1wRUXljDddfe3N082wovX93NSPTDexjE0a+QfP9XX9FCPQFxiSM/f2rD1jTa+jBCULaOXSsgdJn8j+/gDjoiEZ6UUM539XEB3704DLR5uXXgSgGI0Q3kH925SfbfQD43Ty9L4ojueWuy0ax+oVkyqiTM5kP2d7iz+2aLDStb5fffhTnQbHjaw8//e0tNyr16h2zhurCvR8rGjbPDPChITqQeJmAQY5wAzRLdie0J
      - name: george
        pubkey: ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCfTZoVxapLk1sTsBWwWZTL8FVC88+hEG2Ipja61MC0kutYbfy12O3y2/RARYso75I3IYkLVJKHimfGfAZZBvUJGHUlcYsgDJo1ikKvEnfofuIxQwF3d9HQAO4Lujd3rJAhBUwWz7J//KP/n0JyrXWwBXSMP8hrJmspy6U8bL2v73ZMZjlY7YSBYvh4TANYXYv5YgkIToc1kXtFq/ZTXZ8VbD953/1kEqxLzoa0g6jstDDu8E/XUW3dp4ZZSZAcrnxW/CJYNMtCHE62toQkSK7c+eCE4cGJN8nTF4xsYZOVkFAoXDPuv5eDT2GtADdBAnLyPWN50oVjsd7QAXEoJKjh
    standard_user:
      - name: paul
        pubkey: ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCHeTNFZjNIZ54llZTcFuzCTHxyH2ikiagBy0gJtDQSvduCFNylKpATBSetyqpaOwC6NWPSBl41/+oxuqhYwHUOQwQwbZuDSY9HeAx6eJUrB58lRtDzg8ODcZdcW20Wk+o1TIbKBtUiQi8MUxwlV4TRB8GYpKKyi50K4BksIqSEg0Gjr27X6DzWEM/6sjBnyHF2BALdYu2ulTbq6c8Lj1A1sUDHvxVCxPmod0rDhpB10xnMZlttAcS2vNsL7Em02W40Ul0YWkheIfnoX5TPZiPVvEnkInycc35sssP9YAUKodeO5Qw8XYZNt2V6lmObry/fS0Cqg1FOq67GkSzMESQT
      - name: ringo
        pubkey: ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDTDmHemcHOwrbzsC1HUrHS2wshHBN7fS69IVhZHs/uGORyUETcRMcTGSrM9hR9RU2KPwSU7L4+f2oFTOq/swBv14Pk/1xn4npV9RMK1wB86odfQH3/mmtE10sn/SkBmSrqDSb/WVz2aa8+lEA81bIO10NhVK+paE2R12QFVOAxDOcUxDm+GqtlwIdIoX83vMA/THglCdP7RwgFZoeI+AZTG9dlZ6/5/UEGI+fu2RblVWqEuw/9R0SmWGdsOZoWFxQZf7NXxSYNJZ9K8F00rwEcwDT6/eieVh5yYC45Xp+NuKqLOMEPvK/gD8WWuoNHyRJHSLFOkzNi9K3W+z9NUsKV
    allowed_ssh_users:
      - zinzendorf
    other_packages:
      - emacs
      - htop
      - cowsay
    hostname: ramesses
```

## License

CC-BY-4.0

## Author Information

https://plume.baucum.me
