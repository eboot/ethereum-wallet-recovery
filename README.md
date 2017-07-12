# ethwallet-pwdlouskac
based on pyethrecover modified by me for using keystore v3 json file to help recover your lost password if you know some phrases.
using both brute and wordlist technique, start + end words, whole ascii or just numbers

## dependency install:
sudo apt-get install python-pip python-dev libssl-dev build-essential automake pkg-config libtool libffi-dev libgmp-dev

## python modules to require:
sudo pip install pbkdf2 rlp ethereum joblib

## usage:

1. python louskac.py  #eth wallet password tester
    - -h        # help
    - -p file   # keystore ethereum wallet file
    - -z file   # starting words separated by line
    - -k file   # ending words separated by line
    - -v N      # number of threads of jobs
    - -w file   # wordlist file
    - -b arg    # bruteforce type
        - ASCII # whole ascii table
        - whatever char by char eg. 1234567890 or @#!$%^&*(

2. python generuj.py -h #wordlist generator

### examples generuj.py:
 
  python generuj.py -s "fist,second,third"      # makes all possible combinations of words separated by comma.
  python generuj.py -v input.txt                # makes all possible combinations of words inside file input.txt separated by comma.

  generated wordlist will be in same directory with name wordlist_01.txt. 
  When wordlist reach maximum file size 50MB then new file will be created with next name wordlist_02.txt

### examples louskac.py:
  #### bruteforce numbers from 0 to 9 with size of 2
  python louskac.py -p UTC--2017-07-12T00-06-42.772050600Z--f5751c906091b98be2a6be5ce42c573d704aedab -b 1234567890 -d 2
  
  #### bruteforce @#! with size of 3
  python louskac.py -p UTC--2017-07-12T00-06-42.772050600Z--f5751c906091b98be2a6be5ce42c573d704aedab -b @#! -d 3
  
  #### bruteforce whole ASCII table with size of 4 
  python louskac.py -p UTC--2017-07-12T00-06-42.772050600Z--f5751c906091b98be2a6be5ce42c573d704aedab -b ASCII -d 4
  
  #### bruteforce numbers from 0 to 9 with size of 2 and starting words from file start.txt separated by lines
  python louskac.py -p UTC--2017-07-12T00-06-42.772050600Z--f5751c906091b98be2a6be5ce42c573d704aedab -b 1234567890 -d 2 -z start.txt
  
  #### bruteforce numbers from 0 to 9 with size of 4 and ending words from file end.txt separated by lines
  python louskac.py -p UTC--2017-07-12T00-06-42.772050600Z--f5751c906091b98be2a6be5ce42c573d704aedab -b 1234567890 -d 2 -k end.txt
  
  #### use words from wordlist generated by generuj.py
  python louskac.py -p UTC--2017-07-12T00-06-42.772050600Z--f5751c906091b98be2a6be5ce42c573d704aedab -w wordlist_01.txt
  
  #### use starting words from file start.txt and words from wordlist generated by generuj.py
  python louskac.py -p UTC--2017-07-12T00-06-42.772050600Z--f5751c906091b98be2a6be5ce42c573d704aedab -z start.txt -w wordlist_01.txt
  
  
  #### use ending words from file end.txt and words from wordlist generated by generuj.py
  python louskac.py -p UTC--2017-07-12T00-06-42.772050600Z--f5751c906091b98be2a6be5ce42c573d704aedab -w wordlist.txt -k end.txt
  
  
