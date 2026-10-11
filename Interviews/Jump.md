
|Requirement (from posting)|Where it shows up in the interview|
|---|---|
|Linux/UNIX "including advanced commands and shell scripts"|Pipelines, text processing, process/file/network inspection, writing a small script live|
|Practical working knowledge of Python|Small automation tasks: parse logs, call subprocess, handle errors|
|Networking: routing, multicast, ethernet|"How does a packet get from A to B", multicast group joins, ARP, VLANs, debugging with tcpdump|
|Monitor health/performance of a real-time trading platform|Troubleshooting methodology, latency/CPU/memory/IO diagnosis|
|Troubleshoot complex system, software, and network issues|"Service X is slow, walk me through it"|
|Change control, incident management, documentation|Behavioral/ops-mindset questions, how you handle pressure|

Note: the posting does not mention HPC. Your HPC background is a strength (CPU pinning, NUMA, interconnects, performance analysis), but lead with Linux, networking, and troubleshooting.

---

## The one mental model to fix your `|` and `>` gap

Every Unix process starts with three file descriptors: 0 (stdin), 1 (stdout), 2 (stderr). Shell syntax is just wiring between them.

- `cmd > file` points fd 1 at a file. `>>` appends. `2> file` redirects stderr. `2>&1` points fd 2 at wherever fd 1 currently goes.
- `a | b` connects a's stdout to b's stdin through a kernel pipe. Both run at the same time.
- `<` points fd 0 at a file. `<(cmd)` presents a command's output as a file.
- Most tools are small filters (read stdin, write stdout), so you build behavior by chaining them.

Try predicting the output before running each:

```
ls /etc /nonexistent > out.txt            # what lands in out.txt? what prints?
ls /etc /nonexistent > out.txt 2>&1       # now?
ls /etc /nonexistent 2>&1 > out.txt       # why does this differ from the line above?
```

If you can explain that last one (redirections are processed left to right), you understand the model.

---

## Resources

### 1. Shell and command-line fundamentals (start here)

- The Linux Command Line (William Shotts, free book): https://linuxcommand.org/tlcl.php (read the chapters on redirection, pipelines, and "Searching for Files", then text processing)
- MIT Missing Semester: https://missing.csail.mit.edu/ (lectures 1, 2, 4, 5: shell, shell scripting, data wrangling, debugging/profiling)
- Greg's Wiki Bash Guide: https://mywiki.wooledge.org/BashGuide
- Bash FAQ: https://mywiki.wooledge.org/BashFAQ and Bash Pitfalls: https://mywiki.wooledge.org/BashPitfalls (the pitfalls page is gold for scripting interviews)
- Linux Journey: https://linuxjourney.com/ (short, structured lessons)
- explainshell: https://explainshell.com/ (paste any command, get each piece explained)
- ShellCheck: https://www.shellcheck.net/ (lints your scripts and explains why)
- Linux man pages online: https://man7.org/linux/man-pages/ (also just use `man`, `tldr`, and `help` locally)
- Arch Wiki (you already live here): Bash, Core utilities, systemd, and Network configuration pages at https://wiki.archlinux.org/

### 2. Practice with real feedback

- OverTheWire Bandit: https://overthewire.org/wargames/bandit/ (forces you to use find, grep, pipes, ssh, and file inspection)
- Exercism Bash track: https://exercism.org/tracks/bash
- HackerRank Linux Shell domain: https://www.hackerrank.com/domains/shell
- Julia Evans' zines and posts (Bite Size Linux, Bite Size Networking, Bite Size Bash): https://wizardzines.com/ and https://jvns.ca/

### 3. Text processing tools to get fluent in

Learn these as a set: `grep`/`rg`, `sed`, `awk`, `cut`, `sort`, `uniq -c`, `tr`, `xargs`, `find`, `tee`, `head`/`tail -f`, `wc`, `jq`.

- GNU coreutils manual: https://www.gnu.org/software/coreutils/manual/coreutils.html
- GNU grep, sed, and awk manuals: https://www.gnu.org/software/grep/manual/ , https://www.gnu.org/software/sed/manual/ , https://www.gnu.org/software/gawk/manual/
- jq manual: https://jqlang.github.io/jq/manual/

### 4. Troubleshooting and performance (core of the role)

- Brendan Gregg, Linux performance: https://www.brendangregg.com/linuxperf.html (the "60-second analysis" checklist and the USE method are very interview-friendly)
- Tools to know: `top`/`htop`, `vmstat`, `iostat`, `mpstat`, `free`, `ss`, `lsof`, `strace`, `perf`, `dmesg`, `journalctl`, `sar`
- Google SRE Book (incident response, monitoring, postmortems): https://sre.google/sre-book/table-of-contents/
- Linux kernel docs on procfs: https://docs.kernel.org/filesystems/proc.html

### 5. Networking (routing, multicast, ethernet)

- Practical Networking: https://www.practicalnetworking.net/ (clear articles on ethernet, ARP, VLANs, routing, subnetting)
- Beej's Guide to Network Programming: https://beej.us/guide/bgnet/ (sockets, including UDP and multicast concepts)
- Kurose and Ross, Computer Networking: A Top-Down Approach (lecture videos on YouTube) for the layered picture
- iproute2: learn `ip addr`, `ip link`, `ip route`, `ip neigh`, plus `ss`, `tcpdump`, `ethtool`, `traceroute`/`mtr`, `dig`. Man pages at https://man7.org/linux/man-pages/man8/ip.8.html
- tcpdump primer and filter syntax: https://www.tcpdump.org/manpages/pcap-filter.7.html
- Wireshark user guide: https://www.wireshark.org/docs/wsug_html_chunked/
- Multicast: read RFC 1112 (host extensions for IP multicasting) https://www.rfc-editor.org/rfc/rfc1112 and a good IGMP/PIM overview. Be able to explain: what a group address is (224.0.0.0/4), how a host joins (IGMP), how routers build trees (PIM), why trading firms use multicast for market data (one send, many receivers, no per-subscriber copies)
- Low-latency Linux tuning (relevant to why Jump cares): Erik Rigtorp's guide https://rigtorp.se/low-latency-guide/ (CPU isolation, IRQ affinity, NUMA, huge pages, turbo/C-states; overlaps with your HPC knowledge)

### 6. Python for ops/automation

- Automate the Boring Stuff: https://automatetheboringstuff.com/
- Python docs: `subprocess`, `argparse`, `pathlib`, `re`, `socket`, `logging`
- Practice: rewrite your shell one-liners as Python scripts and vice versa, and know when each is the right tool

### 7. Interview question banks

- Linux sysadmin interview questions (community list): https://github.com/chassing/linux-sysadmin-interview-questions
- Classic questions to be able to answer out loud: what happens when you type `ls` and press enter; what happens when you type a URL into a browser; how does a process get created (fork/exec); what is a zombie vs orphan; what do load average numbers mean; difference between a hard and soft link; how does TCP handshake and teardown work; what happens when a disk fills up (and when inodes run out); how would you find what is listening on port 8080

---

## Suggested plan (adjust to your interview date)

1. Days 1-2: Shell model (redirection, pipes, exit codes, quoting, globbing). Do Bandit levels 0-15 and Missing Semester lectures 1-2.
2. Days 3-4: Text processing drills with grep/sed/awk/sort/uniq/xargs on real logs (`journalctl`, `/var/log`, a big CSV). Goal: top-N from a log with no Python.
3. Days 5-6: Troubleshooting. Do Gregg's 60-second checklist on your own machine while running a CPU, memory, and IO hog (`stress-ng`) and narrate what you see.
4. Days 7-9: Networking. Capture your own traffic with tcpdump, trace ARP, DNS, and a TCP handshake. Use `ip` for everything. Study multicast conceptually, then try joining a group with a small Python socket script across two network namespaces (`ip netns`).
5. Days 10+: Mock interviews. Talk through scenarios out loud ("a trading process is dropping packets, go").

Daily habit: for one week, forbid yourself the GUI and any command you already know. Every time you reach for a basic tool, ask "is there a pipeline that does this better?"

---

## Prompt to give other Claude instances (copy-paste ready)

```
You are my Linux and systems tutor. I am a Georgia Tech CS student (rising junior) preparing for a Systems Engineer internship interview at Jump Trading (Trading Infrastructure, Chicago). The posting requires: Linux/UNIX including advanced commands and shell scripts, practical Python, networking concepts (routing, multicast, ethernet), troubleshooting complex system/software/network issues, and operating clearly under pressure. I already use Arch Linux daily, but only know basic commands and task-specific one-offs. I almost never use pipes, redirection, or other shell syntax. I also have HPC and computer architecture background, so you can use CPU/memory/OS concepts as anchors.

How I want to learn:
- Build from first principles. Explain the underlying mechanism (file descriptors, processes, kernel, packets) before the syntax, so I can derive commands instead of memorizing them.
- Do NOT hand me solutions by default. Give me a task or question, let me attempt it, then give targeted feedback on only what I got wrong. Do not re-explain things I got right.
- Use small, concrete, runnable examples I can try on my own Arch machine. Predict-then-run exercises are ideal: ask me what a command will output before I run it.
- Be direct and concrete. If I am wrong, say so plainly and show a working example. Skip generic advice and long preambles.
- Keep output minimal and scoped to what I asked. No comprehensive dumps unless I request one.
- If I say "just show me", give the answer with a short explanation of why it works.

Session structure:
1. Ask me which topic to work on (shell pipelines/redirection, text processing with grep/sed/awk, scripting, process/performance troubleshooting, networking with ip/ss/tcpdump, multicast, Python automation, or mock interview) unless I already named one.
2. Ask 1-2 quick questions to gauge my current level on it.
3. Give me exercises that ramp from simple to interview-level. After each of my answers, correct only the gaps.
4. When I ask, run a mock interview: ask one realistic question at a time (including "X is slow/broken, walk me through your debugging"), wait for my answer, then critique my approach, ordering, and communication under pressure.
5. End each session with a 3-bullet list of what I should drill next.

Start by asking what topic I want to cover today.
```