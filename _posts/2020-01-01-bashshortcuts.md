---
layout: post
title: Some Bash shortcuts
published: true
tag: Bash
---



Some Bash shortcuts that we need to learn. Download the pdf from [here]({{ site.url }}/assets/pdf/bash_cheatsheet.pdf).



## MOVING
C+xx   # toggle cursor position from current position to bol


C+a/e  # move cursor to the bol/eol


C+left/right # move cursor by words to the left/right


## EDITING
C/A+t  # transposes two characters/words


A+l/u  # converts the characters from the cursor position to the end of the word to lowercase/uppercase


A+c    # capitalizes word


C+v    # makes the next character typed verbatim


## DELETE 
C+k    # deletes forward from cursor position to eol  


C+u    # deletes backward from cursor position to bol


A+D/delete # deletes forward from cursor position to to bow/eow


C+w    # deletes the word behind the cursor


C+y    # retrieves last item deleted


## HISTORY
A+p/n  # reverse/forward search in history list


A-</>  # move to top/bottom of history list


C+r    # reverse incremental search in history list


C+o    # execute the current item in the history list and advance to the next one. This is handy if you are trying to re-execute a sequence of commands in the history list.


AC-y    # insert first argument from previous command


A-.    # insert last argument from previous command


!!     # repeats the last command


!n     # re-executes command number n in history line



## USEFUL
C+c    # halts the current command


C+z    # stops the current command, resume with fg or bg


C+l    # clears screen


## NOT USEFUL
C+d    # deletes one character backward or logs out of current session (mainly used for this purpose)


C+h    # deletes one character under cursor (same as DELETE)


C+j/m    # same as RETURN


C+b/f  # move cursor backward/forward one character (same as left/right arrows)


A+b/f  # move cursor backward/forward one word (same as C+left/right arrows)


C+p/n  # previous/next line in history list (same as up/down arrow)


!`blah`   # re-executes command starting with `blah` (useful only if you want to repeat last command, !! is a better alternative)

