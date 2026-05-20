Скрипт:


#!/bin/bash

#Перебор директорий процессов
for pid in /proc/[0-9]*; do

#Создание переменной PID. 
#basename  удаление пути, оставляем только имя
    	
		PID=$(basename "$pid")

#Проверка  можно ли прочитать файл /proc/PID/status
    
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



	
	
	
	

done
