---
layout: post
title: 5th hackathon
date: 07/07/2017
---

## alo news

During the past couple of weeks the `alo` package was enriched with two packages to deal with the conversion of 
the MCH mapping from Run2 format to the yet-to-be-precisely-define Run3 format : 

- `jsonmap/creator`
	- this one is reading the AliRoot mapping (from AliRoot data files) and writes the mapping information into JSON files

- `jsonmap/reader`
	- this one is reading the JSON files created above and do "something" with them. 
	- the something is either creating C++ code to define the new mapping (WIP) or converting into SVG for web display (also WIP)
	
The reading/writing of JSON files is handled by the [RapidJSON](http://rapidjson.org) library. For the web proof-of-concept
 I'm currently doing it "by hand" in some Javascript.

The actual format of the JSON files is still a moving target, but the first goal is to insure all the information required
 to rebuild a complete mapping is there.
 
 Usage:
 ```
 > mch-mapping-convert-to-json
 ```
 
 will produce (in addition to some console pollution that will enventually be removed...) some JSON files :
 
 ```
-rw-r--r--  1 laurent  staff    18K Jul  7 16:59 berg.json
-rw-r--r--  1 laurent  staff   695K Jul  7 16:59 bp.json
-rw-r--r--  1 laurent  staff   4.0K Jul  7 16:59 ch.json
-rw-r--r--  1 laurent  staff   4.8K Jul  7 16:59 ddl.json
-rw-r--r--  1 laurent  staff    63K Jul  7 16:59 de.json
-rw-r--r--  1 laurent  staff   1.6M Jul  7 16:59 motif.json
-rw-r--r--  1 laurent  staff   7.4K Jul  7 16:59 motifs.list.txt
-rw-r--r--  1 laurent  staff   2.4K Jul  7 16:59 motiftypes.aliroot.txt
-rw-r--r--  1 laurent  staff   2.1K Jul  7 16:59 padsize.json
-rw-r--r--  1 laurent  staff    37K Jul  7 16:59 pcb.json
-rw-r--r--  1 laurent  staff   231K Jul  7 16:59 seg.json
```

and some `txt` files used to compare some basic information about the motif types. 
Comparision which  lead to the discovery of a strange thing in station2. Bug or feature, that's still the question...
 
 - [berg.json]({{ site.url }}/assets/2017-07-5th-hackathon/berg.json) is describing the mapping between the Berg connector 
  (the one one the detection elements) pins and the manu channels. That is a file that will change for Run3 with
   the change from manus to dual sampas.
   
   
 
 ## Achieved during the Hackathon
  
 The main achievement is probably the writing of [first tests](https://github.com/mrrtf/alo/blob/master/jsonmap/creator/testMapping.cxx) 
 using  [Boost test framework](http://www.boost.org/doc/libs/1_64_0/libs/test/doc/html/index.html), the testing framework currently
 used by O2.




