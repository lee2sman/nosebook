---
layout: post
title: "Command Line Incantations"
categories: [open source, open source, programming, permacomputing]
---

![A beautiful bright projection of a glitched screen]({{"/images/screen.webp" | absolute_url}} "A beautiful bright projection of a glitched screen")

These are command line shell snippets for useful utilities, often referred to as *incantantions* due to their resemblance to magic spells I suppose. I've written previously on [Why I use the command line](https://leetusman.com/nosebook/why-cli), and [Command line alternatives to cloud products and platforms](https://leetusman.com/nosebook/bash-alternatives). For an intro to using the command line, there are many introductions online, or check out my old workshop notes for [Intro to the Command Line](https://github.com/lee2sman/ITPCampSessionNotes/blob/master/IntroToCommandLine_ITPCamp.md).

Getting started with the command line does feel magical as you start to learn just how easy and fast it can be. But it takes time building up your spellbook. This page aims to be a place to find many of these starter scripts. Adapt and improve them to your needs.

This is a living page. I will try to return and add more snippets to this page over time.

For many more [one-liner](https://en.wikipedia.org/wiki/One-liner_program) command line incantations, check out [Commandlinefu](https://www.commandlinefu.com). For an extensive how-to guide to using [ffmpeg](https://ffmpeg.org/), the magical audiovisual recorder and converter, check out [ffmprovisr](https://amiaopensource.github.io/ffmprovisr/). For more info on [imagemagick](https://imagemagick.org/), check out its website for extensive documentation. [pandoc](https://pandoc.org/) document converter also has great documentation.

## File conversions - Video

### Convert between video file formats.

This converts between formats without re-encoding.

dependencies:
* ffmpeg

```
ffmpeg -i input.avi -c:v copy -c:a copy output.mp4
```

### Trim out a section of a video file

You can specify the start time and total length of time to record. In the snippet below we've specified 1 minute in (00:01:00) to begin and to keep 20 seconds of time from that point (0:0:20).

dependencies:
* ffmpeg

```
ffmpeg -vcodec copy -acodec copy -i inputvideo -ss 00:01:00 -t 0:0:20 outputvideo
```

### Convert video to audio file

dependencies:
* ffmpeg

```
ffmpeg -i input.mp4 -f mp3 output.mp3
```

### Convert folder of images to a video

This takes all jpeg photos in a folder (in alphanumeric order) and stitches them together to form a video file. 

dependencies:
* ffmpeg

```
ffmpeg -framerate 30 -pattern_type glob -i '*.jpg' -c:v libx264 -pix_fmt yuv420p output.mp4
```

## File conversions - Text

### Concat (combine one after another) pdf files

Combine all of the pdf files in a folder.

dependencies:
* ghostscript

```
gs -dBATCH -dNOPAUSE -q -sDEVICE=pdfwrite -sOutputFile=output.pdf *.pdf
```
 
### markdown to pdf

Convert a markdown file to a pdf file.

dependencies:
* pandoc 
* weasyprint 

```
pandoc -s input.md --pdf-engine weasyprint -o output.pdf
```

### pdf to plaintext

This has evolved to a more complex script that converts pdf pages to images, OCR scans each of them, runs a spell checker with autocorrect, then recombines them together into a single text file.

dependencies:
* tesseract-ocr
* ghostscript
* sed
* aspell

[code gist](https://gist.github.com/lee2sman/3c38b7767a59e7437cbc7dc93cbf5e05)

## File conversion - Audio

### Wave file to mp3

Convert audio between formats.

dependencies:
* sox

```
sox input.wav output.mp3
```

## Other Audio

### Trim audio recording down to one second 

Take any length any file and trim it to a smaller section.

dependencies:
* sox

```
sox input.wav output.wav trim 0 1
```

### Concat (Combine one after another) two audio files 

Place audio snippets one after another in a new file.

dependencies:
* sox

```
sox a.wav b.wav c.wav concatenated.wav
```

### Combine audio (mix sound on sound)

Blend two sound files together.

dependencies:
* sox

```
sox -m a.wav b.wav c.wav mixed.wav
```

### Reduce volume by 12dB

Change volume of a file.

dependencies:
* sox

```
sox speech.wav output.wav gain -12
```

### Play internet radio 

There are many dedicated internet radio streaming programs, such as [pyradio](https://leetusman.com/nosebook/pyradio-open-source-alternative), which has a nice text user interface, but this simple command works too.

dependencies:
* sox

```
play -t mp3 https://infraordinary.fiveradiostations.com:8443/stream
```

### Add reverb to audio

Add some reverb to dry sound recordings.

dependencies:
* sox

```
sox input.wav output.wav reverb 50 50 100
```

## Other file manipulation

### Rename files ordered numerically - Bash shell

This snippet renames all jpg files in a directory from alphabetic to numeric order. The `02d` means generate file numbers 00-99. Use `3d` for 000-999. 

```bash
i=1
for f in *.jpg 
    do mv "$f" "$( printf "%02d.jpg" $i )" 
    ((i++))
done
```

### Rename files ordered numerically - Fish shell

```fish
set i 1
for f in *.jpg
    mv "$f" (printf "%02d.jpg" $i)
    set i (math "$i + 1")
end
```

## Web Design

### Starter CSS

This is an example of a minimal CSS stylesheet to help make a site with article text easier to read. This blog and website for example is built up from a starter like this.

```CSS
body { 
  max-width: 65ch; 
  padding: 0.5rem; 
  margin: 0 auto;
}

blockquote {
  border-left: 0.25rem solid darkseagreen;
  padding-left: 1rem;
}
```
