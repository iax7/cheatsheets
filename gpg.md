# GPG

## Symmetric
### Encrypt
`gpg -c secret.txt`
### Decrypt
`gpg -d secret.txt.gpg`

## Asymmetric
### Create Keys
`gpg --gen-key`
### View Keys
`gpg -k`
```
gpg: checking the trustdb
gpg: marginals needed: 3  completes needed: 1  trust model: pgp
gpg: depth: 0  valid:   1  signed:   0  trust: 0-, 0q, 0n, 0m, 0f, 1u
/home/iax/.gnupg/pubring.kbx
----------------------------
pub   rsa2048 2017-09-27 [SC]
      EBE40B2737388D6D5AC5BE6BD9E2A6F649CFCD8D
uid           [ultimate] Isaias Piña <ipina@live.com.mx>
sub   rsa2048 2017-09-27 [E]
```
### Export Pub Key
`gpg --output iaxpub.gpg --export EBE40B2737388D6D5AC5BE6BD9E2A6F649CFCD8D`
as ASCII code `gpg --armor --output key --export EBE40B2737388D6D5AC5BE6BD9E2A6F649CFCD8D`
### Upload Pub Key to server
`gpg --send-keys --keyserver pgp.mit.edu EBE40B2737388D6D5AC5BE6BD9E2A6F649CFCD8D`
### Import Pub Key
`gpg --import iaxpub.gpg`
### Download Pub Key from server
`gpg --keyserver pgp.mit.edu --recv-keys 18384645`

### Encrypt
`gpg -e --recipient(-r) 18384645 secret.txt`

### Decrypt
`gpg -d secret.txt.gpg`


## File sign
### Sign & Encrypt
`gpg (-u [PRIVADA]) --sign killer.sh`
detached `gpg --armor --detach-sign secret.txt`
### Verify
`gpg --verify file`
detached `gpg --verify killer.sh.asc killer.sh`
