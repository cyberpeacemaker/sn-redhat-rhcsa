```shell
top, ps (aux a j), pgrep
grep "model name" /proc/cpuinfo 
&, fg (%), bg (%), jobs
Ctrl + Z
kill (-l)
```

- [address space, security properties, threads, state], [variable, scheduling context, allocated resources], [fork, exec, exit]
- [running R, sleeping[S, D, K, I], Stopped [T, T], zombie [Z, X ]]
- job control [running, stpped, done], (+/-) indicatator, {S, T, S+}
TODO: 417

"
#!/bin/bash
touch ~/bin/.$(basename $0)
while true; do
        var=1
        while [[$var -lt 50000]]; do
                (($var++))
        done
        sleep 1
done

"
