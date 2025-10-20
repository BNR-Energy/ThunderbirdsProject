# Introduction

This project is intended as an exampel how to use submodules to add a generic 
PLC project to a customer specific Twincat solution.


This is the main project containing the generic PLC and customer specific
project.

# How to submodule

To add a submodule:

	git submodule add git@github.com:BNR-Energy/HPU.git

To get the latest version from the remote (Github):

	git submodule update --remote

To commit and push changes that were made in the submodule use common commands
like commit, push etc.

It is adviced to spit the submodule repository in mininum 2 branches. For
example master and dev. Where the new develeopment is done in the Dev branch and
the projects that depend on the submodule use the Master branch. By default the
Master branch is used in the submodule.

To change the branch of the submodule use the following commands in the root of
your project:

	git config -f .gitmodules submodule.HPU.branch dev
	git submodule update --remote
Checkin and push these changes to the remote.