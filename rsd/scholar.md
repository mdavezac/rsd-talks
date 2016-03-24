---
title: The Craftsperson And The Scholar
author: James Hetherington, __Mayeul d'Avezac__
layout: default
slidelink: True
---

Mayeul d'Avezac
------------------

* PhD, Université Pierre et Marie Curie
    * writing code for material science
* Post-doc, NREL
    * writing code for material science
* Engineer in the Research Software Development group, UCL

The State of Research Software
================================

PhDWare
-------

  * Don't look if anyone's done it before
  * Code till it works
  * Generate a figure
  * Throw it away

> * used by the group for next decade
  * though no one understands how it does what it does

Labware
-------

* Understood by that one guy
* Implements great science, now
* FORTRAN in any language
* Code not engineered for readability
* Can't add new science

HPCWare
-------

* Get a 5% improvement in performance
* On a particular architecture
* Publish a scaling graph
* Selection against:
      * Readability
      * Maintainability
      * Adaptability

ConsultantWare
--------

* Little understanding of the science
* Overengineered
* Unmaintainable by the research group

Research Software Developers
============================

The Craftsperson And The Scholar
----------------------------

![](assets/scholar.jpg)

Research Software Engineers
----------------------------

![](generated/RSD_Venn.png)

Research Software Engineers
----------------------------

* Not independent researchers
    * No personal research agenda
* Facilitative, supportive, and collaborative
    * Part of the academic community
    * Deep engagement with research groups
    * Understand, study, and be part of group research activities
    * Can read and understand the papers
* Sustainable and long term
    * Institutional memory
    * Continuity, stability, maintainance

Why it works
------------

* People *want* to be RSEs
* We have been hiding as:
    * RAs who program too much
    * HPC or research group sysadmins
* The research system needs to
    * Measure and incentivise RSEs correctly
    * Integrate RSEs within HEIs
    * Support institutional innovation

UCL Research Software Development
=================================

Governance
----------

![](generated/governance.png)

Activities
----------

* Projects
* Consulting
* Training
* Infrastructure

Domain
------

* From HPC codes to simple scripts
* From theoretical physics to digital humanities

UCL Staffing
------------

* 3 Permanent Roles (Central IT funding)
* Five grant-funded Research Software Developers

Call for projects
-----------------

* Judged by academic panel
* Idealy quarter
* Half FTE for term
* Worth £8k
* Ten projects so far

Paid Projects
-------------

* Via research grants
* Or existing college money
* Displaces free calls
    * Until recruit
* Secured £0.5M (Roughly 33% success rate)
* Total income to UCL ~£1.5M

Sample free projects
====================

Low-Template DNA
----------------

![](assets/whodunnitdna.jpg)

Whodunnit code: low-template DNA
-----------------------

* Low-template DNA
* Relative likelihood of defence and prosecution hypotheses
* Optimise over relative degree of contribution from various individuals

Structural work on likeLTD
--------------------------------------------

* Broken down into functions
* Separate objective function from simulated annealing optimiser
* Look at using different optimiser libraries
* Documentation added
* Ready for publication to CRAN
* Continuous testing to ensure correctness

Performance Improvements in likeLTD
-------------------------------------------

* 4 times from moving to core algorithm to C
* 8 times from parallelisation
* 10 times from change of optimisation algorithm
* 300 times total

Performance Improvements in likeLTD
-----------------------------------

![](assets/ltdFigure.jpg)

DCProgs
=======

Single Ion-Channel
------------------

<figure class="half">
![](assets/Patch_clamp.png) ![](assets/pa.gif)
</figure>

Old State of the Code
-----------------

* Very old-style Fortran
* Hasn't compiled since 2006
* Underpins Nature-published research

New State
---------

* Reimplemented in C++ and Python
* Use linear algebra and root finding libraries
* Just as performant as the Fortran

HemeLB Setup Tool
=================

HemeLB Setup Tool
-----------------

![](assets/tubes.png)

Voxelisation
------------

![](assets/blockgrid.jpg)


Robustness
----------

![](assets/cgal.png)

Robustness
----------

* From ~95% to 100%.
* Voxelisation in the loop

ORACC
-----

![](assets/oracc.jpg)

Purify
------

![](assets/ska.png)

Zacros
------

![](assets/zacros.png)

* Started as free project
* Continued using local funds
* Won ARCHER eCSE
* First commercial sale January 2015

Priorities
==========

Priorities
----------

* Readability
* Reliability
* Performance

**In that Order**

Priorities
----------

* Readability
* Reliability
* Deployability
* Sustainability
* Replicability
* Usability
* Performance

Sources of Software Culture
===========================

Sources of Software Culture
---------------------------

* Enterprise software
* Web software
* Research Software

Agile Processes
---------------

* Short work cycles
* Controlled meetings
* Iterative development
* Customers inside the team
* Collaboration not contract

Continuous Delivery
-------------------

* Release early
* Release often
* Use DevOps for automated deployment

Test Driven Development
-----------------------

* Test everything
* Test first
* Test all the time
* Use tests as specs

Infrastructure
--------------

* Version Control
* Issue Tracking
* Code Review
* Code sharing
* Continuous Integration
* DevOps

Code Management Infrastructure
==============================

Github
------

![](assets/github_intro.png)

Issue Tracking
--------------

![](assets/issues.png)

Pull Requests
-------------

![](assets/pull.png)

Social Coding
-------------

![](assets/social.png)

Testing
=======

You don't need to test if:
--------------------------

> * Your programs always work correctly, or
> * You don't care if they're correct or not, so long
    as their output looks plausible, and
> * You like being inefficient:
    the more you invest in quality, the less total time
    it takes to build working software


Tests As Specifications
-----------------------

Testing tells you:

> * If the program is doing what it's supposed to
> * What the program actually is supposed to do
> * Tests are runnable specifications:
> * Less likely to fall out of sync with the program
    than documentation

Levels of Testing
-----------------

> * Regression testing: Does my code work the same as yesterday
> * Functional testing: Does my code match an analytic solution
> * Unit testing: Does this subroutine work as expected

Continuous Testing Infrastructure
---------------------------------

![](assets/jenkins-logo.png)

Jenkins
-------

![](assets/jenkins-front.png)

Cross-platform Testing
----------------------

![](assets/systems.png)

Automation
==========

How Things Should Be
--------------------

``` Bash
fetch_dataset 53b6
run_model dataset_53b6
examine_results results_28_02_13_1_53b6_98d2
archive_results latest
create_graphs results_28_02_13_1_53b6_98d2
```

Program or Be Programmed
------------------------

* Repetition Leads to Boredom
* Boredom Leads To Horrifying Mistakes
* Horrifying Mistakes Leads to God-I-Wish-I-Was-Still-Bored

-- Will Larson

Automation is Reproducibility
-----------------------------

* Computational research can be *more* reproducible than other methodologies
* Currently it is less; how often do we replicate computational experiments?
* Automated research is Auditable Research

This talk's Makefile
--------------------

``` make
%-reveal.html: %.md
	$(PANDOC) $(PANDOCARGS) $< -o $@

%.png: %.py
	python $< $@

%.png: %.nto
	neato $< -T png -o $@

%.png: %.dot
	dot $< -T png -o $@
```

This Talk On Jenkins
--------------------

``` yaml
jobs:
  - 'talks-publisher':
     repo: UCL/rsd-talks
     directory: output-site
     exec: make
```

This talk on [GitHub](https://github.com/UCL/rsd-talks): https://github.com/UCL/rsd-talks

Publishing from Jenkins with Puppet
-----------------------------------

``` puppet
define jenkins_config::web_publish (
  $job="${title}-publisher",
  $from="output",
  $to=$title,
  ) {

  file {"${name}_${job}_${from}":
    path => "/etc/httpd/conf.d/${name}.conf",
    content => template('jenkins_config/web_publish.erb'),
      owner   => 'apache',
      notify  => Service['httpd']
  }
}
```

Training
========

Training
--------

* classes:
    * [Research Software Engineering With Python](http://development.rc.ucl.ac.uk/training/engineering)
    * [Research Computing with C++](http://development.rc.ucl.ac.uk/training/rcwithcpp)
* With research groups during projects
* And...

Software Carpentry
------------------

![](assets/ssi_carpentry.jpg)

Software Carpentry
------------------

* Intensive "bootcamp"
* Automation
* Version control
* Unit testing
* Databases

> I found the command line intimidating at first, but after a while it felt
> like I was inside my computer.

-- A student at a UCL software carpentry event

Coda
====

Acknowledgements
----------------

* Clare Gryce, Gavin McLachlan, Mike Cope, Rex Knight
* Anthony Finkelstein, Richard Catlow, David Price, John Shawe-Taylor, Simon Arridge, Peter Coveney
* Timo Betcke, Michail Stamatakis, David Balding, Miguel Bernabeu, Remis Lape, David Colquhoun
* Eleanor Robson, Jason McEwen, David Holder, Sebastien Ourselin
* Mayeul D'Avezac, Jens Nielsen, Gary Macindoe, Raquel Alegre, Sinan Shi, Tom Pollard
* Dirk Gorissen, Simon Baxter, Ilian Todorov, Rob Haines
* Neil Chue Hong, Simon Hettrick, Kenji Takeda, David de Roure
* Ana Nelson, Kohsuke Kawaguchi
* Andrew Smith, Ben Waugh, Matt Clarkson
* Greg Wilson

Why you should have one
-----------------------

* More and more research uses software
* General programmers can't understand research
* Postdocs and PhD students don't have time to make *reliable* code
* Bad code will hold research back
* Longuer know-how retention across generations of student
* Better software for better research

Why you should be one
---------------------

* write code
* while doing all sorts of science
* and humanities

Why you should be one
---------------------

![](assets/dilstein.png)
