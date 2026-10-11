## Build the simulator (in container)

```bash
cd ~/sesc
make                # builds sesc.opt
ls                  # confirm sesc.opt / sesc.debug links
```

Only `sesc.opt` was built in P0. Re-run `make` after every simulator edit, and build `sesc.debug` if a later handout needs it.

---

## Build a Splash2 app (example: lu)

```bash
cd ~/sesc/apps/Splash2/lu
make                # produces lu.mipseb
```

---

## Run a simulation

```bash
rm -f sesc_lu.mipseb.n128.rpt    # ALWAYS delete the old report first (reports append and merge)
~/sesc/sesc.opt -fn128.rpt -c ~/sesc/confs/cmp4-noc.conf -olu.out -elu.err lu.mipseb -n128 -p1
```

|Flag|Meaning|
|---|---|
|`-f<str>`|Report file is `sesc_<exe>.<str>` (no space after `-f`)|
|`-c <conf>`|Config file (space required)|
|`-o<file>`|App stdout (no space)|
|`-e<file>`|App stderr (no space)|
|`-n<N>`|lu matrix size|
|`-p<N>`|Core count (use 1 until Project 3)|

Paste dashes as plain minus signs (Word turns them into long dashes).

### Verify the run finished

```bash
cat lu.err          # should be empty
tail lu.out         # should end with "Total time without initialization: 0"
```

---

## Read results

```bash
~/sesc/scripts/report.pl sesc_lu.mipseb.n128.rpt
~/sesc/scripts/report.pl sesc_lu.mipseb.n*.rpt     # wildcards: one summary per file
```

|Field|Meaning|
|---|---|
|Sim Time|Simulated (target) execution time|
|Exe Time|Real (native) time the simulator took|
|nInst|Completed dynamic instructions|
|Total / RAS / BPred|Branch predictor accuracy: overall, return stack, direction predictor|
|BJ|% of instructions that are control flow|
|IPC|Instructions per cycle|
|Busy, MisBr, LDQ, STQ, IWin, ROB, Regs, TLB|Where cycles went (percentages)|

---

## Compile your own C program for the simulator

```bash
cd ~/sesc/tests
gcc -o hello hello.c && ./hello      # sanity check natively first

/mipsroot/cross-tools/bin/mips-unknown-linux-gnu-gcc -O0 -g -static -mabi=32 -fno-delayed-branch -fno-optimize-sibling-calls -msplit-addresses -march=mips4 -o hello.mipseb hello.c

~/sesc/sesc.opt -fhello0.rpt -c ~/sesc/confs/cmp4-noc.conf -ohello.out hello.mipseb
```

Run from the directory containing `hello.mipseb`, and don't add a path to it.

---

## Inspect the binary

```bash
export PATH=$PATH:/mipsroot/cross-tools/bin    # optional: skip the long path

mips-unknown-linux-gnu-objdump -d hello.mipseb > hello.dump   # disassembly; search for <main>
mips-unknown-linux-gnu-strip hello.mipseb                     # strip symbols
mips-unknown-linux-gnu-addr2line -e hello.mipseb <addr>       # address -> file:line
```

Other tools in `cross-tools/bin` use the same `mips-unknown-linux-gnu-` prefix (`g++`, `gas`, etc.).


## Docker (host machine)

|Task|Command|
|---|---|
|Is PROJ running?|`docker ps`|
|Start it|`docker start PROJ`|
|Open a shell|`docker exec -it PROJ bash` (add `-u <user>` if you land in root)|
|List volumes|`docker volume ls`|
|See PROJ's mounts|`docker inspect PROJ --format '{{json .Mounts}}'`|
|Back up work to host|`docker cp PROJ:/home/<user>/sesc ~/backup/`|
|Pull a file out|`docker cp PROJ:/home/<user>/sesc/apps/Splash2/lu/sesc_lu.mipseb.n128.rpt .`|
