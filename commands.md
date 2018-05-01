# Commands I keep forgetting

## Linux

#### Drop I/O caches:

```bash
echo 3 | sudo tee /proc/sys/vm/drop_caches
```

#### [Use Intel syntax with `objdump -d`](https://stackoverflow.com/a/10369792/2212455):

```bash
objdump -M intel intel-mnemonic -d «file»
```

#### [Make a port forward to an UNIX socket](https://unix.stackexchange.com/a/293308/50044):

```bash
ncat -l 0.0.0.0 «port» --sh-exec 'ncat -U «socket»'
```

#### [Set up remote port forwarding](http://blog.trackets.com/2014/05/17/ssh-tunnel-local-and-remote-port-forwarding-explained-with-examples.html):

```bash
ssh -R «remote port»:localhost:«local port» «server» sleep infinity
```

#### [Inter-device `mv`](https://serverfault.com/a/565307):

```bash
rsync -abmv --remove-source-files «source» «destination»
```

#### Start a MariaDB server with Docker:

```
docker run --name «container name» -e MYSQL_DATABASE=«name» -e MYSQL_USER=«username» -e MYSQL_PASSWORD=«password» -e MYSQL_RANDOM_ROOT_PASSWORD=1 mariadb
```

#### Start a PostgreSQL server with Docker:

```
docker run --name «container name» -e POSTGRES_DB=«name» -e POSTGRES_USER=«username» -e POSTGRES_PASSWORD=«password» postgres
```

#### [Use POSIX access control lists](http://wazniak.mimuw.edu.pl/images/a/ae/Bsi_01_lab.pdf):

```bash
setfacl -m u:«username»:rwx «paths» # set access
setfacl -d -m u:«username»:rwx «directories» # default for new files inside directories
setfacl -bn «paths» # remove ACL
```

## Android

#### Install Arch Linux in chroot container:

```bash
dd if=/dev/zero of=arch.img bs=1M count=2048
mke2fs -t ext4 -L arch arch.img
mkdir -p /arch
mknod -m a=rwxrwxrwx /dev/block/loop255 b 7 255
losetup /dev/block/loop255 arch.img
mount /dev/block/loop255 /arch
chroot /arch /bin/bash
```

## LaTeX

#### [Add a website to BibLaTeX `.bib` file](https://tex.stackexchange.com/questions/35977/how-to-add-a-url-to-a-latex-bibtex-file):

```tex
@misc{bworld,
  author = {Ingo Lütkebohle},
  title = {{BWorld Robot Control Software}},
  howpublished = "\url{http://aiweb.techfak.uni-bielefeld.de/content/bworld-robot-control-software/}",
  year = {2008}, 
  note = "[Online; accessed 19-July-2008]"
}
```

#### Vertically align minipages:

```tex
\usepackage{adjustbox}

\adjustbox{valign=t}{\begin{minipage}{0.6\textwidth}
  \includegraphics[width=.9\textwidth]{foo.png}
\end{minipage}}
\adjustbox{valign=t}{\begin{minipage}[b]{0.4\textwidth}
  \lipsum[20]
\end{minipage}}
```
