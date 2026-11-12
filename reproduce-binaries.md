# Export + hashing notes

Done in Ubuntu Server 26.04.1 VM (UTM), not on host. ISO SHA-256 checked against Canonical SHA256SUMS first. Screenshot of the compared hashes available in `COMP3010 - PCAP Analysis evidence.pdf`at repo root.

```
# VM
sudo apt install -y tshark

# host - serve pcap, Ctrl+C straight after
python3 -m http.server 8000

# VM
wget http://192.168.64.1:8000/COMP3010CW1.pcap
cp COMP3010CW1.pcap /tmp/   # permission denied reading from ~, fine from /tmp (not entirely sure why)
tshark -r /tmp/COMP3010CW1.pcap --export-objects http,/tmp/rout > /dev/null
sha256sum /tmp/rout/*
```

| File | SHA-256 |
|---|---|
| gerv.gun | 0931537889c35226d00ed26962ecacb140521394279eb2ade7e9d2afcf1a7272 |
| trow.exe | 94a0a09ee6a21526ac34d41eabf4ba603e9a30c26e6a1dc072ff45749dfb1fe1 |
| wp.exe | 79d503165d32176842fe386d96c04fb70f6ce1c8a485837957849297e625ea48 |

Screenshot of full output in evidence folder.
