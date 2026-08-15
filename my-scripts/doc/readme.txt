1) create a new repo on github

git clone git@github.com:RobertBerger/meta-rauc.git

2) add my-scripts dir

cd meta-rauc

echo "# meta-rauc fork" >> README.md

git init

git add .

git commit -m "first commit"

#git remote add origin git@github.com:RobertBerger/meta-arm.git

git push -u origin master

3) use my repo

mv meta-rauc meta-rauc.ori
git clone git@github.com:RobertBerger/meta-rauc.git

4) add upstream

cd meta-rauc

git remote add official-upstream https://github.com/rauc/meta-rauc.git

$ git fetch official-upstream

warning: no common commits
remote: Enumerating objects: 2766, done.
remote: Counting objects: 100% (1066/1066), done.
remote: Compressing objects: 100% (546/546), done.
remote: Total 2766 (delta 662), reused 521 (delta 515), pack-reused 1700 (from 4)
Receiving objects: 100% (2766/2766), 432.22 KiB | 5.14 MiB/s, done.
Resolving deltas: 100% (1445/1445), done.
From https://github.com/rauc/meta-rauc
 * [new branch]      dunfell    -> official-upstream/dunfell
 * [new branch]      gatesgarth -> official-upstream/gatesgarth
 * [new branch]      hardknott  -> official-upstream/hardknott
 * [new branch]      honister   -> official-upstream/honister
 * [new branch]      kirkstone  -> official-upstream/kirkstone
 * [new branch]      krogoth    -> official-upstream/krogoth
 * [new branch]      langdale   -> official-upstream/langdale
 * [new branch]      master     -> official-upstream/master
 * [new branch]      mickledore -> official-upstream/mickledore
 * [new branch]      morty      -> official-upstream/morty
 * [new branch]      nanbield   -> official-upstream/nanbield
 * [new branch]      pyro       -> official-upstream/pyro
 * [new branch]      rocko      -> official-upstream/rocko
 * [new branch]      scarthgap  -> official-upstream/scarthgap
 * [new branch]      styhead    -> official-upstream/styhead
 * [new branch]      sumo       -> official-upstream/sumo
 * [new branch]      thud       -> official-upstream/thud
 * [new branch]      walnascar  -> official-upstream/walnascar
 * [new branch]      warrior    -> official-upstream/warrior
 * [new branch]      whinlatter -> official-upstream/whinlatter
 * [new branch]      wrynose    -> official-upstream/wrynose
 * [new branch]      zeus       -> official-upstream/zeus

...

5) use specific upstream branch and make our own branch

git co remotes/official-upstream/master

5.1) we want commit: 01f7e1bbde162263bcfb93fd5a3bcdd1483f688c

git co 01f7e1bbde162263bcfb93fd5a3bcdd1483f688c

git branch 2026-08-11-training

git co 2026-08-11-training

5.3) push upstream

git co master
cd my-scripts
./push-all-to-github.sh




#5) use specific upstream branch/commit and make own branch
#
#syntax: git fetch url-to-repo branchname:refs/remotes/origin/branchname
#
#$ git fetch git://github.com/STMicroelectronics/meta-st-stm32mp dunfell:refs/remotes/origin/dunfell
#
#From git://github.com/Freescale/meta-freescale
# * [new branch]        dunfell    -> origin/dunfell
#

#6) Update from upstream:
#git co master
#>> git remote -v
#
#official-upstream       git://github.com/Freescale/meta-freescale (fetch)
#official-upstream       git://github.com/Freescale/meta-freescale (push)
#origin  git@github.com:RobertBerger/meta-freescale.git (fetch)
#origin  git@github.com:RobertBerger/meta-freescale.git (push)
#
#>> git fetch official-upstream
#remote: Counting objects: 4043, done.
#remote: Compressing objects: 100% (1273/1273), done.
#remote: Total 4043 (delta 3130), reused 3632 (delta 2727)
#Receiving objects: 100% (4043/4043), 721.50 KiB | 402.00 KiB/s, done.
#Resolving deltas: 100% (3130/3130), completed with 502 local objects.
#From git://git://github.com/Freescale/meta-freescale
#   62591d9..e758547  master     -> official-upstream/master
# + 2942327...a382678 master-next -> official-upstream/master-next  (forced update)
#   a3fa5ce..6a1f33c  morty      -> official-upstream/morty
#---
#

6) hack the branch and update

6.1) hack it

6.2) add/commit

6.3) What was changed?

$ git diff 2021-06-09-3ba7567532bcda55d9d73deff80a350877b68d07-pd21.1.0-stm-dunfell --stat
 conf/layer.conf                                                           | 2 +-
 recipes-bsp/u-boot/{u-boot_2020.01.bbappend => u-boot_2020.01.bbbbappend} | 0
 2 files changed, 1 insertion(+), 1 deletion(-)

7) push upstream:
git co master
cd my-scripts
./push-all-to-github.sh

#8) apply patches
#
#cd meta-virtualization
#
#git co 2019-09-09-warrior-2.7+
#
#stg init
#
#stg series
#
#stg import --mail ../meta-virtualization-patches/2019-09-09-warrior-2.7+/0001-use-systemd-as-cgroup-manager-for-docker-While-it-s-.patch
#
#import all patches
#
#...
#
#stg series
#
#stg commit --all
#
#git log
#
#git co master
#
9) push to my upstream

my-scripts/push-all-to-github.sh

