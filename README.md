# org-agenda-archive #

A command-line tool written in Python to archive your emacs orgmode agenda items for a certain year.  Most
work is done by the [orgparse](https://github.com/karlicoss/orgparse) package by Karlicoss.  Entries for which
the NEWEST year matches the target year are archived in a different file with the same headings tree
structure.  For example, an entry labelled as created in 2021 but with clock times and closed in 2022 will be
archived if 2022 is the target year, but NOT if 2021 is the target.  The rest are kept in a third (cleaned)
file.  The program will refuse to overwrite any files.

My headings tree looks something like this:
```orgmode
* Research
** Project 1
*** TODO Task
*** Appointment
** Project 2
* Teaching
** Class 1
*** TODO task
** Class 2
* Other
** Meetings
*** Etc.
```

This allows me to view clocked time per project or class, but also for all research or teaching, or simply all
work.  Keeping this structure in my archive files allows me to do the same for ancient times if necessary.


## Example use ##

```text
$ org-agenda-archive -h
usage: org-agenda-archive [-h] [-v | -q] fileName matchYear

Archive orgmode agenda items for a certain year.

positional arguments:
  fileName       name of the orgmode agenda file to process
  matchYear      entries matching this year will be archived

optional arguments:
  -h, --help     show this help message and exit
  -v, --verbose  produce progress output (e.g. for debugging) (default: False)
  -q, --quiet    produce no (error) output (e.g. for cron job) (default: False)
```

```text
$ org-agenda-archive Work.org 2019

Any entries from the year 2019 will be archived in Work-archive-2019.org,
all other entries will be kept in Work-cleaned-2019.org

Sections found in Work.org:    24
Entries archived in Work-archive-2019.org:   357
Entries kept in Work-cleaned-2019.org:   617
```


## Known bugs ##

* If the last section (level 1) is empty, it is lost.
* Any empty subsection (level 2) is lost?


## Author and licence ##

* Copyright: 2020-2024, Marc van der Sluys
* Contact:   https://marc.vandersluys.nl
* Licence:   [GPLv3+](https://www.gnu.org/licenses/gpl.html)


### How to thank me ###

In order of increasing gratitude:
1. Use more open-source software for whatever it is you are doing.
1. Contribute to other open-source-software projects.
1. Create and publish your own open-source software package.

