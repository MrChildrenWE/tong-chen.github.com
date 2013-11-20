---
title: transferLong2ShortNameSpecialColumn.py
author: 悟道
layout: post
permalink: /?p=2925
categories:
  - scripts
---
<table>
  <tr cellpadding=0><td>
    热度:
  </td><td cellpadding=0><img src='http://210.75.224.29/wordpress/wp-content/plugins/statpresscn/images/sun.gif' width=10 height=10 border=0 /></td><td cellpadding=0><img src='http://210.75.224.29/wordpress/wp-content/plugins/statpresscn/images/sun_dark.gif' width=10 height=10 border=0 /></td><td cellpadding=0><img src='http://210.75.224.29/wordpress/wp-content/plugins/statpresscn/images/sun_dark.gif' width=10 height=10 border=0 /></td><td cellpadding=0><img src='http://210.75.224.29/wordpress/wp-content/plugins/statpresscn/images/sun_dark.gif' width=10 height=10 border=0 /></td><td cellpadding=0><img src='http://210.75.224.29/wordpress/wp-content/plugins/statpresscn/images/sun_dark.gif' width=10 height=10 border=0 /></td></tr>
</table>

<pre class="brush: python; title: transferLong2ShortNameSpecialColumn.py; notranslate" title="transferLong2ShortNameSpecialColumn.py">#!/usr/bin/env python
# -*- coding: utf-8 -*-
#from __future__ import division, with_statement
'''
Copyright 2010, 陈同 (chentong_biology@163.com).
Please see the license file for legal information.
===========================================================
'''
__author__ = 'chentong & ct586[9]'
__author_email__ = 'chentong_biology@163.com'
#=========================================================
import sys

def labelP(num, alphabet):
division = num / 26
remain = num % 26
label = ''
label = alphabet[remain] + label
while division &gt; 25:
remain = division % 26
division = division / 26
label = alphabet[remain-1] + label
#---------------------------
if division &gt; 0:
label = alphabet[division-1] + label
return label
#-----------------------------------


def main():
if len(sys.argv) &lt; 3:
print &gt;&gt;sys.stderr, "Print the result to screen, and a map file \
with_a suffix .Name_Map."
print &gt;&gt;sys.stderr, "Transfer sequence locus from long name to \
short name of given column for any text file separated by tab ."
print &gt;&gt;sys.stderr, 'Using python %s filename given_col[1 \
based] header [default 0] output_map_table[default 1 means yes, \
accept 0 means no]' % sys.argv[0]
sys.exit(0)
#-------------------------------------------
col = int(sys.argv[2]) - 1
if len(sys.argv) &gt; 3:
header = int(sys.argv[3])
else:
header = 0
if len(sys.argv) &gt; 4:
ot_map_table = sys.argv[4]
else:
ot_map_table = '1'
alphabet = [chr(i) for i in range(97,123)]
i = 0
#print ot_map_table
if ot_map_table == '1':
print &gt;&gt;sys.stderr, "here"
map40 = sys.argv[1] + '.Name_Map'
fh = open(map40, 'w')
oldname = ''
for line in open(sys.argv[1]):
if header:
print line,
header -= 1
continue
#-----------------------------
lineL = line.split('\t')
curname = lineL[col]
if curname == oldname:
i -= 1
else:
oldname = curname
#--------------------------------------
lineL[col] = labelP(i,alphabet)
if ot_map_table == '1' and curname != oldname:
print &gt;&gt;fh, " %s\t%s" % (curname, lineL[col])
print '\t'.join(lineL),
i += 1
#-----------------end file-------------------------------
if ot_map_table == '1':
fh.close()
if __name__ == '__main__':
main()
</pre>