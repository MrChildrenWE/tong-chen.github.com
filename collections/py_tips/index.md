---
title: Python tips
author: ct
layout: page
---

1. UnicodeDecodeError: 'ascii' codec can not decode byte 0xe9 in position 0: ordinal not in range(128))

   ```python
   import sys
   reload(sys)
   sys.setdefaultencoding('utf8')
   ```

2. 启动HTTP服务

   ```python
   cd specific_dir_containing_an_index.html
   python -m SimpleHTTPServer 11521 # 11521 as port number
   ```

3. Generate a combination for all elements in a 2-d list.

   ```python
   def iterateLists(optL, resultL, recordL=[]):
       '''
       optL = [
               ["-p prot1", "-p prot2", "-p prot3"], 
               ["-l chem1", "-l chem2"], 
               ["-o result"]
              ]
       
       recordL: tmp record variable
   
       resultL = [
           ["-p prot1", "-l chem1",  "result"], 
           ["-p prot1", "-l chem2",  "result"]
       ]
   
       '''
       if debug:
           print >>sys.stderr, "New"
           print >>sys.stderr, optL
           print >>sys.stderr, recordL
       for opt in optL[0]:
           newOptL = optL[1:]
           if len(newOptL) > 1:
               tmpL = recordL[:]
               tmpL.append(opt)
               if debug:
                   print >>sys.stderr, "Next"
                   print >>sys.stderr, newOptL
                   print >>sys.stderr, tmpL
               iterateLists(newOptL, resultL, tmpL)
           else:
               for last_opt in newOptL[0]:
                   tmpL = recordL[:]
                   tmpL.append(opt)
                   tmpL.append(last_opt)
                   resultL.append(tmpL)
   #------------------------------------
   a = a = [[1],  [2,  3],  [4,  5],  [6]]
   resultL = []
   iterateLists(a, resultL)
   resultL
   [[1, 2, 4, 6], [1, 2, 5, 6], [1, 3, 4, 6], [1, 3, 5, 6]]
   ```
















