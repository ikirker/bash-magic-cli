# bash-magic-cli

This is a work-in-progress bash reimplementation of [@slackhq](https://github.com/slackhq/)'s [magic-cli](https://github.com/slackhq/magic-cli).

The idea is to make a collection of related commands in separate scripts look like one command in one script. I originally started reimplementing it because on the HPC clusters we work on we change up environment variables a lot, so especially things that depend on scripting languages can break if something becomes not available or changes version from the one the author expected. Originally I started it in Golang, because this would give a static binary that would be impervious enough, but doing it in bash instead seemed easier to update on the clusters.

