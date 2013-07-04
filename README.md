multigit
========

Perl wrapper for easily multiplying git commands to a selection of configured repositories.

## Installation:

Copy `multigit` into your execution path.
Copy `.multigit.conf` into your home directory and modify it to your liking.

## Usage example:

Assuming the configuration file as it were would be correct for you -- which it is not! --
you would have these git repositories configured for `multigit`:

 - /usr/work/hal9000/base
 - /usr/work/hal9000/persistence
 - /usr/work/hal9000/reasoning
 - /usr/work/hal9000/logic
 - /usr/work/hal9000/speech\_synthesis
 - /usr/work/hal9000/light\_control
 - /usr/work/hal9000/air\_lock
 - /usr/work/hal9000/life\_support
 - /usr/work/hal9000/camera

and you would have grouped the repositories like this:

 - Backend systems: base, persistence, reasoning and logic
 - Frontend systems: speech\_synthesis and light\_control
 - Interfaces: air\_lock, life\_support and camera

In your current project you work with these repositories:
 - base
 - persistence
 - light\_control
 - air\_lock

Therefore you set the `defaultParams` to `BP1v`.

Typical workflow:

 - `multigit checkout master`
 - `multigit pull`
 - `multigit checkout -b new_branch`
 - work in those repositories:
 - `multigit diff`
 - `multigit commit -am "A very helpful commit message"`
 - ...
 - `multigit push`

## Remarks:

 - `multigit` delegate anything to `git`. It just moves into the correct repositories first,
   therefore it is irrelevant from where you call it.

 - You can sequence multiple git commands using a command delimiter (defaults to %%), e.g. `multigit co master %% pull %% status`

 - For usage on your coding machine you should set your `defaultParams` to include every repository.
   `multigit`s output includes the parameter values for each repository so that you can easily adapt your
   command line string.

 - For usage on a specialized system you can set yout `defaultParams` to ignore everything not relevant there.

 - It may be useful to set up some aliases for different repository presets, like:
   - alias mgFoo ='multigit -BP1v'
   - alias mgBar ='multigit -Bv'
