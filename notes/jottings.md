Looking at the data above a little bit further:
```
dur = 1.02 seconds
proto = tcp
dir = ->
tot_pkts = 4
tot_bytes = 276
src_bytes = 156
label = Background-Established
```

**Numerical features:**
- `dur`: duration of connection
- `tot_pkts`: total # of packets exchanged
- `tot_bytes`: total # of bytes exchanged
- `src_bytes`: # bytes sent from the source

**Categorical features:**
- `proto`: protocol
- `dir`: direction of flow
- `state`: TCP state
- `stos/dstos`: type of service