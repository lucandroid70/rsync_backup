# rsync_backup
Simple script for copy of backup your file and folders 



#!/bin/sh

START_TIME=`date +%Y-%m-%d_%H:%M:%S`;
if [ ! -e '/home/lucandroid70/libri_2' ]; then   # '/home/lucandroid70/libri_2' insert you folder DESTINATION 
	MISSING_PATH=1
	echo -n Missing_destination_path:_ >> /home/lucandroid70/libri_2/log/logluca.log  # '/home/lucandroid70/libri_2/log/log.log' insert you file log 
else
	MISSING_PATH=0
rsync --archive --human-readable --verbose --stats --log-file=/home/lucandroid70/libri_2/log/logluca.log.details '/home/lucandroid70/Scrivania/libri' '/home/lucandroid70/libri_2'   
fi


if [ $? -eq 0 ] && [ $MISSING_PATH -eq 0 ]; then
   STOP_TIME=`date +%Y-%m-%d_%H:%M:%S`;
   echo "$START_TIME $STOP_TIME Backup successful: Source: [/home/lucandroid70/Scrivania/libri] Destination: [/home/lucandroid70/libri_2]" >> /home/lucandroid70/libri_2/log/logluca.log
else
   STOP_TIME=`date +%Y-%m-%d_%H:%M:%S`;
   echo "$START_TIME $STOP_TIME Backup failure:    Source: [/home/lucandroid70/Scrivania/libri] Destination: [/home/lucandroid70/libri_2]" >> /home/lucandroid70/libri_2/log/logluca.log
fi


# source - destination you have idea for insert your folder ;)
# LucaAndroid70  ;)
