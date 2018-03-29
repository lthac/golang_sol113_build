# golang_sol113_build
Instructions to build Golang in Solaris 11.3

```
mkdir code
cd code/
pkg install git gcc system/header rsync developer/object-file
mkdir /usr/local
git clone https://go.googlesource.com/go
cd go ; git checkout release-branch.go1.4 ; cd src
CC=/usr/bin/gcc ./all.bash
rsync -az ~/code/go /usr/local/
git checkout -- ..
git clean -df
git checkout release-branch.go1.10
git pull
CC=/usr/bin/gcc GOROOT_BOOTSTRAP=/usr/local/go ./all.bash
mv /usr/local/go/ /usr/local/go1.4
mv ~/code/go/ /usr/local/go1.10

root@solaris:~# uname -a
SunOS solaris 5.11 11.3 i86pc i386 i86pc
root@solaris:~# /usr/local/go1.10/bin/go version
go version go1.10.1 solaris/amd64
```

