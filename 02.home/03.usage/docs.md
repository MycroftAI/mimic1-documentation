---
title: Usage
taxonomy:
    category:
        - docs
---

## Usage

By default mimic will play the text using an audio device. Alternatively it can
output the wave file in RIFF format (often called `.wav`).

#### Read text

- To an audio device
  ```
  $ ./mimic -t TEXT
  ```
  
  **_Example_**
  ```
  $ ./mimic -t "Hello. Doctor. Name. Continue. Yesterday. Tomorrow."
  ```

- To an audio file
  ```
  $ ./mimic -t TEXT -o WAVEFILE
  ```
  
  **_Example_**
  ```
  $ ./mimic -t "Hello. Doctor. Name. Continue. Yesterday. Tomorrow." -o hello.wav
  ```

#### Read text from file

- To an audio device
  ```
  $ ./mimic -f TEXTFILE
  ```
  
  **_Example_**
  ```
  $ ./mimic -f doc/alice
  ```

- To an audio file
  ```
  $ ./mimic -f TEXTFILE -o WAVEFILE`
  ```
  **_Example_**
  ```
  $ ./mimic -f doc/alice -o hello.wav
  ```

#### Change voice

- List available internal voices
  ```
  $ ./mimic -lv
  ```

- Use an internal voice
  ```
  $ ./mimic -t TEXT -voice VOICE
  ```
  
  **_Example_**
  ```
  $ ./mimic -t "Hello" -voice slt
  ```

- Use an external voice file
  ```
  $ ./mimic -t TEXT -voice VOICEFILE
  ```
  
  **_Example_**
  ```
  $ ./mimic -t "Hello" -voice voices/cmu_us_slt.flitevox
  ```

- Use an external voice url
  ```
  $ ./mimic -t TEXT -voice VOICEURL
  ```
  
  **_Example_**
  ```
  $ ./mimic -t "Hello" -voice http://www.festvox.org/flite/packed/flite-2.0/voices/cmu_us_ksp.flitevox
  ```

###### Notes

- mimic offers several voices that can use different speech modelling techniques
  (diphone, clustergen, hts). Voices can differ a lot on size, naturalness and
  intelligibility.

  * Diphone voices are less computationally expensive and quite intelligible but
    they lack naturalness (sound more robotic). e.g. `./mimic -t "Hello world" -voice kal16`

  * clustergen voices can sound more natural and intelligible at the expense of
    size and computational requirements. e.g.:  e.g. `./mimic -t "Hello world" -voice slt`, `./mimic -t "Hello world" -voice ap`

  * hts voices usually may sound a bit more synthetic than clustergen voices,
    but have much smaller size. e.g.:  e.g. `./mimic -t "Hello world" -voice slt_hts`

- Voices can be compiled (built-in) into mimic or loaded from a `.flitevox` file.
  The only exception are hts voices. hts voices combine both a compiled function with
  a voice data file `.htsvoice`. Mimic will look for the `.htsvoice` file when
  the hts voice is loaded, looking into the current working directory, 
  the "voices" subdirectory and the `$prefix/share/mimic/voices` directory if it
  exists.

- Voice names are identified as loadable files if the name includes a "`/`" 
  (slash) otherwise they are treated as internal compiled-in voices.

- The `voices/` directory contains several flitevox voices. Existing Flite voices
  can be found here: [http://www.festvox.org/flite/packed/flite-2.0/voices/](http://www.festvox.org/flite/packed/flite-2.0/voices/)

- The voice referenced via an url will be downloaded on the fly.

#### Other options

Voices accept additional *debug* options. specified as `--setf feature=value` in the
command line. Wrong values can prevent mimic from working. Some speech modelling
techniques may not implement support for changing these features so at some point
some voices may not provide support for these options. Here are some examples:

- Use simple concatenation of diphones without prosodic modification
  ```
  ./mimic --sets join_type=simple_join doc/intro.txt
  ```

- Print sentences as they are said
  ```
  ./mimic -pw doc/alice
  ```

- Make it speak slower
  ```
  ./mimic --setf duration_stretch=1.5 doc/alice
  ```

- Make it speak faster
  ```
  ./mimic --setf duration_stretch=0.8 doc/alice
  ```

- Make it speak higher
  ```
  ./mimic --setf int_f0_target_mean=145 doc/alice
  ```

See `lang/cmu_us_kal/cmu_us_kal.c`) to see some other features and values.


#### Say the hour

- The talking clock requires a single argument HH:MM. Under Unix you can call it
  ```
  ./mimic_time `date +%H:%M` 
  ```

#### Benchmarking

- For benchmarking, "none" can be used to discard the generated audio and give a summary of the speed:
  ```
  ./mimic -f doc/alice none
  ```


Say something:
```bash
./bin/mimic -t "Hello. Doctor. Name. Continue. Yesterday. Tomorrow."
```

List internal voices:
```bash
./bin/mimic -lv
```

Set voice(internal): 
```bash
./bin/mimic -t "Hello" -voice slt
```

Set voice(file): 
```bash
./bin/mimic -t "Hello" -voice voices/cmu_us_slt.flitevox
```

Set voice(url): 
```bash
./bin/mimic -t "Hello" -voice voices/http://www.festvox.org/flite/packed/flite-2.0/voices/cmu_us_ksp.flitevox
```

Print mimic help info: 
```bash
./bin/mimic -h
```

Help info output:
```text
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