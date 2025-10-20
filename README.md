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

Keep in mind that the submodules point to a specific commit in the main
repostory. This means that after getting a update form the remote submodule a
commit and push of the main project is requred to reflect those changes in the
remote repository. Added benefit is that a change in the remote repository of
a submodule is not directly appied in repositories using that submodule.

It is advised to spit the submodule repository in mininum 2 branches. For
example master and dev. Where the new develeopment is done in the Dev branch and
the projects that depend on the submodule use the Master branch. By default the
Master branch is used in the submodule.

To change the branch of the submodule use the following commands in the root of
your project:

	git submodule update --remote
	git config -f .gitmodules submodule.HPU.branch dev
	git submodule update --remote
	cd hpu
	git checkout dev
Checkin and push these changes to the remote.

# Repository structure

For a customer appliation a repository is created for development of the
customer PLC code. This solution contains 2 PLC projects. One for the project
and a second as a submodule for the machine PLC code.

- ThunderbirdsProject (Main "customer" project)
  - HPU (Submodule project for Machine PLC code)
  - ProjectPanel (Project for customer specific PLC code)

The HPU repository only contains the PLC project. By itself this can not be used
for development becouse it does not contain any IO infomation and other parts
of a complete TwinCAT project. A seperate solution is used for this, this is the
HPUMainProject. This could be seen as the main deveopment repository for the HPU
code, and should have the submodule pointed at the dev branch.

- HPUMainProject
  - HPU (Submodule project for develeopment of Machine PLC code)