---
title: Usage
taxonomy:
    category:
        - docs
---

Say something:
```
./bin/mimic -t "Hello. Doctor. Name. Continue. Yesterday. Tomorrow."
```

List internal voices:
```
./bin/mimic -lv
```

Set voice(internal): 
```
./bin/mimic -t "Hello" -voice slt
```

Set voice(file): 
```
./bin/mimic -t "Hello" -voice voices/cmu_us_slt.flitevox
```

Set voice(url): 
```
./bin/mimic -t "Hello" -voice http://www.festvox.org/flite/packed/flite-2.0/voices/cmu_us_ksp.flitevox
```

Print mimic help info: 
```
./bin/mimic -h
```

Help info output:
```
mimic: a small simple speech synthesizer
  Carnegie Mellon University, Copyright (c) 1999-2011, all rights reserved
  version: mimic-2.0.0-release Dec 2014 (http://cmuflite.org)
usage: mimic TEXT/FILE [WAVEFILE]
  Converts text in TEXTFILE to a waveform in WAVEFILE
  If text contains a space the it is treated as a literal
  textstring and spoken, and not as a file name
  if WAVEFILE is unspecified or "play" the result is
  played on the current systems audio device.  If WAVEFILE
  is "none" the waveform is discarded (good for benchmarking)
  Other options must appear before these options
  --version   Output mimic version number
  --help      Output usage string
  -o WAVEFILE Explicitly set output filename
  -f TEXTFILE Explicitly set input filename
  -t TEXT     Explicitly set input textstring
  -p PHONES   Explicitly set input textstring and synthesize as phones
  --set F=V   Set feature (guesses type)
  -s F=V      Set feature (guesses type)
  --seti F=V  Set int feature
  --setf F=V  Set float feature
  --sets F=V  Set string feature
  -ssml       Read input text/file in ssml mode
  -b          Benchmark mode
  -l          Loop endlessly
  -voice NAME Use voice NAME (NAME can be filename or url too)
  -voicedir NAME Directory contain voice data
  -lv         List voices available
  -add_lex FILENAME add lex addenda from FILENAME
  -pw         Print words
  -ps         Print segments
  -psdur      Print segments and their durations (end-time)
  -pr RelName Print relation RelName
  -voicedump FILENAME Dump selected (cg) voice to FILENAME
  -v          Verbose mode
```  