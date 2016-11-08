# tar-patches
IBM i specific GNU tar patches

This repository contains a set of branches that correlate with a major GNU tar release. Each branch contains a set of directories that correlate with an IBM i release and a directory ```any``` that applies to all IBM i releases.

The way to use this repository is:
- clone the branch specific to your version of GNU tar
- copy the patches from ```any``` to the GNU tar source directory
- copy the patches from the directory specific to your IBM i release to the GNU tar source directory
- Apply each patch with ```patch -p1```

Example: Compiling GNU tar 1.29 on IBM i 7.1

```
tar -xzf tar-1.29.tar.gz
git clone -b 1.29 --single-branch https://github.com/kadler/tar-patches.git patches
cd tar-1.29
cp ../patches/any/*.patch .
cp ../patches/7.1/*.patch .
for f in *.patch
do
  patch -p1 < $f
done
```
