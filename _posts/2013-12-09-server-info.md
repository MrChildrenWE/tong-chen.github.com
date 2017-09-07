---
title: ��ʾ������������Ϣ
author: ct
layout: post
categories:
  - Bash
tags:
  - Bash
  - Bioinfo
---

ѧϰLinux���������Ҫ��һ̨Linux�����������˷����������뿴���������������������Լ�����ǰд��һ���ű���һ���鿴ϵͳ�󲿷ֲ�����

This is an old script used to display the hardware information of a server. Generated infos include hostname, IP, Bits-of-OS, CPU, memory, disk .etc.

```
#!/bin/bash
# -*- coding: UTF-8 -*-

#��Ļ���
echo "This lists the information of this computer."

#�������
echo

##tput setaf [0-7] �Cʹ��ANSIת������ǰ��ɫ
#Color Code for tput:  
#0 �C Black  
#1 �C Red  
#2 �C Green  
#3 �C Yellow  
#4 �C Blue  
#5 �C Magenta  
#6 �C Cyan  
#7 �C White  
##tput sgr0 �C Turn off all attributes 

##`hostname` ����������
#`/sbin/ifconfig` ifconfig��linux��������ʾ�����������豸������ӿڿ���������
# sed -n '2p' ��ʾ�ļ��ĵ�2��
# cut��һ��ѡȡ������ǽ�һ�����ݾ���������ȡ��������Ҫ������
# -d ���Զ���ָ�����Ĭ��Ϊ�Ʊ����-f ����-dһ��ʹ�ã�ָ����ʾ�ĸ�����

echo "Hostname is $(tput setaf 3)`hostname`$(tput sgr0),\
Ip address is $(tput setaf 3)\
`/sbin/ifconfig | sed -n '2p' | cut -d ':' -f 2 | cut -d ' ' -f 1`.
$(tput sgr0)"
#---------------------------------------------------------------------------

#uname -a ����ʾϵͳ�����ڵ����ơ�����ϵͳ�ķ��а�š�����ϵͳ�汾������ϵͳ�Ļ��� ID �š�
# Linux ehbio 2.6.32-642.4.2.el6.x86_64 #1 SMP Tue Aug 23 19:58:13 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
#
nuclear=`uname -a | cut -d ' ' -f 3`
bitInfo=`uname -a | cut -d ' ' -f 12`

# if��䣬�ж�ϵͳ��64λ����32λ
if test $bitInfo == "x86_64"; then
    bit=64
else
    bit=32
fi
#tput bold �C Set bold mode 
#head -n	��ӡÿ���ļ���ǰn�У������Ǵ�ӡĬ�ϵ�ǰ10��
# /etc/issue �鿴ϵͳ��½��Ϣ�����а汾��Ϣ
#
echo "The $(tput bold)${bit}$(tput sgr0) bt operating \
system is $(tput bold) `head -n 1 /etc/issue`\
$(tput sgr0), Nuclear info is $(tput setaf 1)\
${nuclear}$(tput sgr0)."
#��ӡ����

echo
# `sed -n '5p' /proc/cpuinfo �õ����½��model name	: Intel(R) Xeon(R) CPU G7-4809 v2 @ 4.90GHz
#sed 's/[ ] */ /g'ò��ʲôҲû���������ǲ��Եģ���仰�ǰѶ�������ո��Ϊ�����ո�


echo "The CPU is$(tput setaf 4)`sed -n '5p' /proc/cpuinfo \
| cut -d ':' -f 2 | sed 's/[ ] */ /g'`$(tput sgr0)."

echo

echo "There are $(tput setaf 5)\
`cat /proc/cpuinfo | grep "physical id" | sort | uniq \
| wc -l`$(tput sgr0) physical cpu, \
each physical \
cpu has$(tput setaf 5)`sed -n '12p' /proc/cpuinfo | \
cut -d ':' -f 2`$(tput sgr0) cores,\
$(tput setaf 5)`sed -n '10p' /proc/cpuinfo | \
cut -d ':' -f 2`$(tput sgr0) threads."

echo

echo "There are $(tput setaf 5)\
`cat /proc/cpuinfo | grep "cpu cores" | wc -l`$(tput sgr0) logical cpu."

# sedԪ�ַ��� ^ ƥ���п�ʼ���磺/^sed/ƥ��������sed��ͷ���С�* ƥ��0�������ַ����磺/ *sed/ƥ������ģ����һ�������ո�����sed���С�
#sed 's/^ *//g' ɾ����ͷ�Ŀո�


#bc������һ��֧�����⾫�ȵĽ���ִ�еļ��������� bc -l ����ʹ�õı�׼��ѧ��


mem=`head -n 1 /proc/meminfo | cut -d ':' -f 2 | sed 's/^ *//g' | cut -d ' ' -f 1`
memInM=$(echo "$mem/1024/1024" | bc -l)

echo

echo "The memory of this server is $(tput setaf 5)${memInM}$(tput sgr0)G."

echo

echo "The disk information is :"

#linux��df����Ĺ������������linux���������ļ�ϵͳ�Ĵ��̿ռ�ռ��������������ø���������ȡӲ�̱�ռ���˶��ٿռ䣬Ŀǰ��ʣ�¶��ٿռ����Ϣ��
#-h �����Ķ���ʽ��ʾ

echo "`df -h`"
```