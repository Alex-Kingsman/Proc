# Proc



Скрипт;



#!/bin/bash

#Перебор директорий процессов
for pid in /proc/[0-9]*; do

#Создание переменной PID. 
#basename - удаление пути, оставляем только имя
    	PID=$(basename "$pid")

#Проверка - можно ли прочитать файл /proc/PID/status
    if [ -r "$pid/status" ]; then

#Получаем PPID процесса
#"^PPid:"  -ищем строку, начинающуюся с PPid в файле status
#awk '{print $2}' -выводим второй столбец
        PROC_PPID=$(grep "^PPid:" "$pid/status" | awk '{print $2}')
		
#Получаем состояние процесса
#Ищем строкиу начинающуюся с State, выводим второй столбец
        STATE=$(grep "^State:" "$pid/status" | awk '{print $2}')
		
		#Получаем имя процесса
        NAME=$(grep "^Name:" "$pid/status" | awk '{print $2}')

#Выводим
        echo "PID: $PID | PPID: $PROC_PPID | STATE: $STATE | NAME: $NAME"

    fi
	
	
	
	
	
	
	
Результат:


sudo bash 1.sh
PID: 1 | PPID: 0 | STATE: S | NAME: systemd
PID: 10 | PPID: 2 | STATE: I | NAME: kworker/0:0H-events_highpri
PID: 1023 | PPID: 1 | STATE: S | NAME: cron
PID: 103 | PPID: 2 | STATE: I | NAME: kworker/R-crypt
PID: 1049 | PPID: 1 | STATE: S | NAME: nginx
PID: 1050 | PPID: 1049 | STATE: S | NAME: nginx
PID: 1051 | PPID: 1049 | STATE: S | NAME: nginx
PID: 1052 | PPID: 1049 | STATE: S | NAME: nginx
PID: 1053 | PPID: 1049 | STATE: S | NAME: nginx
PID: 1056 | PPID: 1 | STATE: S | NAME: agetty
PID: 106 | PPID: 2 | STATE: I | NAME: kworker/1:1H-kblockd
PID: 1061 | PPID: 1 | STATE: S | NAME: fwupd
PID: 1074 | PPID: 1 | STATE: S | NAME: upowerd
PID: 11 | PPID: 2 | STATE: I | NAME: kworker/u8:0-ext4-rsv-conversion
PID: 117 | PPID: 2 | STATE: I | NAME: kworker/R-charg
PID: 12 | PPID: 2 | STATE: I | NAME: kworker/R-mm_pe
PID: 1206 | PPID: 2 | STATE: I | NAME: kworker/u10:2-events_unbound
PID: 1292 | PPID: 2 | STATE: I | NAME: kworker/2:0-cgroup_free
PID: 13 | PPID: 2 | STATE: I | NAME: rcu_tasks_kthread
PID: 14 | PPID: 2 | STATE: I | NAME: rcu_tasks_rude_kthread
PID: 1445 | PPID: 2 | STATE: I | NAME: kworker/u12:0-events_unbound
PID: 1450 | PPID: 2 | STATE: I | NAME: kworker/u11:3-events_unbound
PID: 1452 | PPID: 2 | STATE: I | NAME: kworker/u9:3-events_power_efficient
PID: 1454 | PPID: 1 | STATE: S | NAME: sshd
PID: 1458 | PPID: 1454 | STATE: S | NAME: sshd
PID: 1461 | PPID: 2 | STATE: S | NAME: psimon
PID: 1463 | PPID: 1 | STATE: S | NAME: systemd
PID: 1465 | PPID: 1463 | STATE: S | NAME: (sd-pam)
PID: 15 | PPID: 2 | STATE: I | NAME: rcu_tasks_trace_kthread
PID: 1574 | PPID: 1458 | STATE: S | NAME: sshd
PID: 1575 | PPID: 1574 | STATE: S | NAME: bash
PID: 1589 | PPID: 2 | STATE: I | NAME: kworker/u10:3-events_power_efficient
PID: 1594 | PPID: 2 | STATE: I | NAME: kworker/1:1
PID: 16 | PPID: 2 | STATE: S | NAME: ksoftirqd/0
PID: 1601 | PPID: 2 | STATE: I | NAME: kworker/u11:2-events_unbound
PID: 1684 | PPID: 2 | STATE: I | NAME: kworker/u9:2-writeback
PID: 17 | PPID: 2 | STATE: I | NAME: rcu_preempt
PID: 170 | PPID: 2 | STATE: I | NAME: kworker/1:2-events
PID: 1706 | PPID: 2 | STATE: I | NAME: kworker/u10:0-events_power_efficient
PID: 1708 | PPID: 2 | STATE: I | NAME: kworker/u9:0-events_power_efficient
PID: 171 | PPID: 2 | STATE: S | NAME: scsi_eh_2
PID: 172 | PPID: 2 | STATE: I | NAME: kworker/R-scsi_
PID: 174 | PPID: 2 | STATE: I | NAME: kworker/u12:2-events_power_efficient
PID: 1753 | PPID: 2 | STATE: I | NAME: kworker/0:1-cgwb_release
PID: 18 | PPID: 2 | STATE: S | NAME: migration/0
PID: 19 | PPID: 2 | STATE: S | NAME: idle_inject/0
PID: 2 | PPID: 0 | STATE: S | NAME: kthreadd
PID: 20 | PPID: 2 | STATE: S | NAME: cpuhp/0
PID: 207 | PPID: 2 | STATE: I | NAME: kworker/R-kdmfl
PID: 21 | PPID: 2 | STATE: S | NAME: cpuhp/1
PID: 22 | PPID: 2 | STATE: S | NAME: idle_inject/1
PID: 23 | PPID: 2 | STATE: S | NAME: migration/1
PID: 237 | PPID: 2 | STATE: I | NAME: kworker/R-raid5
PID: 24 | PPID: 2 | STATE: S | NAME: ksoftirqd/1
PID: 26 | PPID: 2 | STATE: I | NAME: kworker/1:0H-kblockd
PID: 27 | PPID: 2 | STATE: S | NAME: cpuhp/2
PID: 276 | PPID: 2 | STATE: S | NAME: jbd2/dm-0-8
PID: 277 | PPID: 2 | STATE: I | NAME: kworker/R-ext4-
PID: 28 | PPID: 2 | STATE: S | NAME: idle_inject/2
PID: 29 | PPID: 2 | STATE: S | NAME: migration/2
PID: 3 | PPID: 2 | STATE: S | NAME: pool_workqueue_release
PID: 30 | PPID: 2 | STATE: S | NAME: ksoftirqd/2
PID: 313 | PPID: 2 | STATE: I | NAME: kworker/0:2-events
PID: 32 | PPID: 2 | STATE: I | NAME: kworker/2:0H-kblockd
PID: 3216 | PPID: 2 | STATE: I | NAME: kworker/2:1-events
PID: 33 | PPID: 2 | STATE: S | NAME: cpuhp/3
PID: 34 | PPID: 2 | STATE: S | NAME: idle_inject/3
PID: 346 | PPID: 1 | STATE: S | NAME: systemd-journal
PID: 35 | PPID: 2 | STATE: S | NAME: migration/3
PID: 36 | PPID: 2 | STATE: S | NAME: ksoftirqd/3
PID: 37 | PPID: 2 | STATE: I | NAME: kworker/3:0-events
PID: 371 | PPID: 2 | STATE: I | NAME: kworker/R-kmpat
PID: 372 | PPID: 2 | STATE: I | NAME: kworker/R-kmpat
PID: 38 | PPID: 2 | STATE: I | NAME: kworker/3:0H-events_highpri
PID: 395 | PPID: 1 | STATE: S | NAME: multipathd
PID: 4 | PPID: 2 | STATE: I | NAME: kworker/R-rcu_g
PID: 415 | PPID: 1 | STATE: S | NAME: systemd-udevd
PID: 422 | PPID: 2 | STATE: S | NAME: psimon
PID: 43 | PPID: 2 | STATE: S | NAME: kdevtmpfs
PID: 44 | PPID: 2 | STATE: I | NAME: kworker/R-inet_
PID: 45 | PPID: 2 | STATE: S | NAME: kauditd
PID: 46 | PPID: 2 | STATE: S | NAME: khungtaskd
PID: 47 | PPID: 2 | STATE: S | NAME: oom_reaper
PID: 482 | PPID: 2 | STATE: I | NAME: kworker/2:2H-kblockd
PID: 49 | PPID: 2 | STATE: I | NAME: kworker/R-write
PID: 5 | PPID: 2 | STATE: I | NAME: kworker/R-rcu_p
PID: 503 | PPID: 2 | STATE: S | NAME: irq/18-vmwgfx
PID: 505 | PPID: 2 | STATE: I | NAME: kworker/R-ttm
PID: 51 | PPID: 2 | STATE: S | NAME: kcompactd0
PID: 52 | PPID: 2 | STATE: S | NAME: ksmd
PID: 54 | PPID: 2 | STATE: S | NAME: khugepaged
PID: 5495 | PPID: 2 | STATE: I | NAME: kworker/u11:0-events_power_efficient
PID: 55 | PPID: 2 | STATE: I | NAME: kworker/R-kinte
PID: 56 | PPID: 2 | STATE: I | NAME: kworker/R-kbloc
PID: 57 | PPID: 2 | STATE: I | NAME: kworker/R-blkcg
PID: 570 | PPID: 2 | STATE: S | NAME: jbd2/sda2-8
PID: 571 | PPID: 2 | STATE: I | NAME: kworker/R-ext4-
PID: 58 | PPID: 2 | STATE: S | NAME: irq/9-acpi
PID: 596 | PPID: 1 | STATE: S | NAME: systemd-network
PID: 6 | PPID: 2 | STATE: I | NAME: kworker/R-slub_
PID: 60 | PPID: 2 | STATE: I | NAME: kworker/R-tpm_d
PID: 61 | PPID: 2 | STATE: I | NAME: kworker/R-ata_s
PID: 619 | PPID: 1 | STATE: S | NAME: systemd-resolve
PID: 62 | PPID: 2 | STATE: I | NAME: kworker/R-md
PID: 63 | PPID: 2 | STATE: I | NAME: kworker/R-md_bi
PID: 632 | PPID: 1 | STATE: S | NAME: systemd-timesyn
PID: 64 | PPID: 2 | STATE: I | NAME: kworker/R-edac-
PID: 65 | PPID: 2 | STATE: I | NAME: kworker/R-devfr
PID: 66 | PPID: 2 | STATE: S | NAME: watchdogd
PID: 68 | PPID: 2 | STATE: I | NAME: kworker/R-quota
PID: 69 | PPID: 2 | STATE: I | NAME: kworker/3:1H-kblockd
PID: 698 | PPID: 2 | STATE: I | NAME: kworker/R-cfg80
PID: 7 | PPID: 2 | STATE: I | NAME: kworker/R-netns
PID: 70 | PPID: 2 | STATE: S | NAME: kswapd0
PID: 7019 | PPID: 2 | STATE: I | NAME: kworker/3:2
PID: 7035 | PPID: 2 | STATE: I | NAME: kworker/2:2
PID: 7036 | PPID: 2 | STATE: I | NAME: kworker/2:3-events
PID: 7037 | PPID: 2 | STATE: I | NAME: kworker/u12:1-events_power_efficient
PID: 7051 | PPID: 1575 | STATE: S | NAME: sudo
PID: 7052 | PPID: 7051 | STATE: S | NAME: sudo
PID: 7053 | PPID: 7052 | STATE: S | NAME: bash
PID: 71 | PPID: 2 | STATE: S | NAME: ecryptfs-kthread
PID: 72 | PPID: 2 | STATE: I | NAME: kworker/R-kthro
PID: 727 | PPID: 1 | STATE: S | NAME: dbus-daemon
PID: 73 | PPID: 2 | STATE: I | NAME: kworker/R-acpi_
PID: 74 | PPID: 2 | STATE: S | NAME: scsi_eh_0
PID: 745 | PPID: 1 | STATE: S | NAME: polkitd
PID: 75 | PPID: 2 | STATE: I | NAME: kworker/R-scsi_
PID: 76 | PPID: 2 | STATE: S | NAME: scsi_eh_1
PID: 77 | PPID: 2 | STATE: I | NAME: kworker/R-scsi_
PID: 771 | PPID: 1 | STATE: S | NAME: systemd-logind
PID: 772 | PPID: 1 | STATE: S | NAME: udisksd
PID: 80 | PPID: 2 | STATE: I | NAME: kworker/R-mld
PID: 81 | PPID: 2 | STATE: I | NAME: kworker/R-ipv6_
PID: 818 | PPID: 1 | STATE: S | NAME: unattended-upgr
PID: 83 | PPID: 2 | STATE: I | NAME: kworker/0:1H-kblockd
PID: 836 | PPID: 1 | STATE: S | NAME: rsyslogd
PID: 84 | PPID: 2 | STATE: I | NAME: kworker/u8:1-ext4-rsv-conversion
PID: 876 | PPID: 1 | STATE: S | NAME: ModemManager
PID: 90 | PPID: 2 | STATE: I | NAME: kworker/R-kstrp
PID: 93 | PPID: 2 | STATE: I | NAME: kworker/u13:0
PID: 94 | PPID: 2 | STATE: I | NAME: kworker/u14:0
PID: 95 | PPID: 2 | STATE: I | NAME: kworker/u15:0
PID: 96 | PPID: 2 | STATE: I | NAME: kworker/u16:0
PID: 97 | PPID: 2 | STATE: I | NAME: kworker/u17:0


	
	
	
	

done
