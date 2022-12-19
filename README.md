# PicoCTF-Wave_a_flag
Write-up for a PicoCTF challenge

Location: https://play.picoctf.org/practice/challenge/170

Category: General Skills

Description: Can you invoke help flags for a tool or binary? [This program] has extraordinarily helpful information...

How to solve:
  1. Hovering over the link for [This program] in the description shows a url. I copied this link and logged into the PicoGym webshell. I then used "wget" + the pasted link to load the file to display this output: 2022-12-19 20:05:59 (182 MB/s) - 'warm.1' saved [10936/10936]
  2. Given the description, I tried running a few commands that did nothing: "warm" "warm -h" "warm --help".
  3. I tried getting a text readout of the file by typing "cat warm" and the output was a bunch of nonsense text. However within that text was the following: "Hello user! Pass me a -h to learn what I can do!-hOh, help? I actually don't do much, but I do have this flag here: picoCTF{b1scu1ts_4nd_gr4vy_f0668f62}I don't know what '%s' means! I do know what -h means though!"
  4. Since the flag was given in that text blob, I was able to solve the puzzle.

Flag: picoCTF{b1scu1ts_4nd_gr4vy_f0668f62}

Notes: It should be clear that my approach was not the intended way to solve for the flag.  Looking into the hints, the idea was to first run "chmod +x warm" to turn the file into an executable. From there, running "./warm" would give you "Hello user! Pass me a -h to learn what I can do!" which would spur you on to try "./warm -h" which would deliver the flag. I can imagine that running "cat [something unknown]" may give you issues if the file was large, or at the very least give you too much output to manually examine.
