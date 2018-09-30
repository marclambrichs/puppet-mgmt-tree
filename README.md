# Build rpm
 
Install necessary libraries
```
$ yum install rpmdevtools
```

Next, we can setup directory tree for our rpm build:
```
$ rpmdev-setuptree
```

This will create a `rpmbuid` directory with necessary subdirs:
```
$ tree rpmbuild
rpmbuild
├── BUILD
├── RPMS
├── SOURCES
├── SPECS
└── SRPMS
```

Create an archive like this:
```
$ cd rpmbuild/SOURCES
$ tar -C ../../puppet-mgmt-tree/ -cvzf puppet-mgmt-tree-1.0.tar.gz etc --transform='s,^,puppet-mgmt-tree-1.0/,'
```

Next, copy SPECS/puppet-mgmt-tree.spec to rpmbuild/SPECS and start the build:
```
$ cp ../../puppet-mgmt-tree/SPECS/puppet-mgmt-tree.spec ../SPECS
$ cd ../..
$ rpmbuild -v -bb rpmbuild/SPECS/puppet-mgmt-tree.spec
```
