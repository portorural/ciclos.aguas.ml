---
title: Anotações do Thinkpad X201i
description: Algumas dicas fundamentais para funcionamento do Arch Linux no X201i dedicado à plataforma Águas ML
published: true
date: 2020-11-11T07:29:34.678Z
tags: thinkpad, x201i
editor: markdown
dateCreated: 2020-11-11T07:29:34.678Z
---

# Arch no Thinkpad X201i
Anotações para o notebook dedicado à plataforma Águas ML

.
## Lembretes úteis

```
sensors-detect
sensors
sudo thinkfan -n
```


.
### Instalando

sudo pacman -S thinkfan

apt install thinkfan

.
### Configure o módulo kernel
Se preferir, acesse a pasta e edit com vi ou nano

```
echo "options thinkpad_acpi fan_control=1" > /etc/modprobe.d/thinkfan.conf
```

### Atualize o módulo kernel
```
modprobe thinkpad_acpi
```

### Configure padrões de configuração para o thinkfan
```
sed -i 's|START=no|START=yes|' /etc/default/thinkfan
sed -i 's|DAEMON_ARGS="-q"|DAEMON_ARGS="-q -b 1 -s 15"|' /etc/default/thinkfan
```

### Verifique seus sensores
```
find /sys/devices -type f -name "temp*_input"
```

### Habilite o serviço no boot
```
systemctl enable thinkfan
exit
```

### Habilite no boot e depois verifique o serviço
```
systemctl enable thinkfan
systemctl status thinkfan.service
```

.
## Thinkfan.conf para o x201/x201i


```
tp_fan /proc/acpi/ibm/fan

# thermal sensors returns weird data so I had to rely on hwmon
#tp_thermal /proc/acpi/ibm/thermal (0, 10, 15, 2, 10, 5, 0, 3, 0, 3)

hwmon /sys/devices/platform/coretemp.0/hwmon/hwmon4/temp2_input
hwmon /sys/devices/virtual/thermal/thermal_zone0/hwmon2/temp1_input
hwmon /sys/devices/virtual/thermal/thermal_zone0/hwmon2/temp2_input

#X201 user specific
#lvl    low     up      RPM
(0,    0,      47)     # 0
(1,    42,     57)     # 2000
(2,    44,     59)     # 3300
(3,    50,     65)     # 3500
(4,    54,     70)     # 3500
(5,    60,     73)     # 3800
(6,    62,     83)     # 3800
(7,    65,     88)     # 4300
(127,  70,     32767)  # 5300

```

.
## Infos do x201i

Página oficial da wiki arch
https://wiki.archlinux.org/index.php/Lenovo_ThinkPad_X201

Lista das versões de BIOS oficiais
https://support.lenovo.com/us/en/downloads/ds013909-bios-update-utility-for-windows-8-32-bit-64-bit-7-32-bit-64-bit-vista-32-bit-64-bit-xp-thinkpad

Intel Core i5-520M (PGA988) CPU
https://www.cpu-upgrade.com/CPUs/Intel/Core_i5_Mobile/i5-520M_(PGA988).html
