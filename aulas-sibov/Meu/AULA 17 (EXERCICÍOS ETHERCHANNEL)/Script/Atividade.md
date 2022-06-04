## EQUIPAMENTO SW1 - F0/2-5
```
en
    conf t
        hostname SW1
        int range f0/2-5
        channel-protocol pagp
        channel-group 1 mode auto
        no shut
        exit
```
## EQUIPAMENTO SW2 - F0/2-5
```
en
    conf t
        hostname SW2
        int range f0/2-5
        channel-protocol pagp
        channel-group 1 mode desirable
        no shut
        exit
        int range f0/6-9
        channel-protocol lacp
        channel-group 2 mode active
        no shut
        exit
```
## EQUIPAMENTO SW3 - F0/6-9
```
en
    conf t
        hostname SW3
        int range f0/6-9
        channel-protocol lacp
        channel-group 2 mode passive
        no shut
        exit
        int range f0/10-13
        channel-protocol pagbp
        channel-group 3 mode on
        no shut
        exit
```
## EQUIPAMENTO SW4 - F0/10-13
```
en
    conf t
        hostname SW4
        int range f0/10-13
        channel-protocol pagp
        channel-group 3 mode on
        no shut
        exit
```