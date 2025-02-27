#Software #Hacking #Principiante
# Definición
How to automate tasks to run at intervals on linux servers? Use ssh to connect to this server:
```
Server: saturn.picoctf.net
Port: 64781
Username: picoplayer 
Password: pYkku7iMsS
```
# Hints
(None)
# Solución
Primero nos conectamos vía [[SSH#Uso de `-vvv` en SSH]] al servidor.

```bash
AsumomezaC-picoctf@webshell:~$ ssh picoplayer@saturn.picoctf.net -p 64781 -vvv
OpenSSH_8.9p1 Ubuntu-3ubuntu0.10, OpenSSL 3.0.2 15 Mar 2022
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: include /etc/ssh/ssh_config.d/*.conf matched no files
debug1: /etc/ssh/ssh_config line 21: Applying options for *
debug3: expanded UserKnownHostsFile '~/.ssh/known_hosts' -> '/home/AsumomezaC-picoctf/.ssh/known_hosts'
debug3: expanded UserKnownHostsFile '~/.ssh/known_hosts2' -> '/home/AsumomezaC-picoctf/.ssh/known_hosts2'
debug2: resolving "saturn.picoctf.net" port 64781
debug3: resolve_host: lookup saturn.picoctf.net:64781
debug3: ssh_connect_direct: entering
debug1: Connecting to saturn.picoctf.net [13.59.203.175] port 64781.
debug3: set_sock_tos: set socket 3 IP_TOS 0x10
debug1: Connection established.
debug1: identity file /home/AsumomezaC-picoctf/.ssh/id_rsa type -1
debug1: identity file /home/AsumomezaC-picoctf/.ssh/id_rsa-cert type -1
debug1: identity file /home/AsumomezaC-picoctf/.ssh/id_ecdsa type -1
debug1: identity file /home/AsumomezaC-picoctf/.ssh/id_ecdsa-cert type -1
debug1: identity file /home/AsumomezaC-picoctf/.ssh/id_ecdsa_sk type -1
debug1: identity file /home/AsumomezaC-picoctf/.ssh/id_ecdsa_sk-cert type -1
debug1: identity file /home/AsumomezaC-picoctf/.ssh/id_ed25519 type -1
debug1: identity file /home/AsumomezaC-picoctf/.ssh/id_ed25519-cert type -1
debug1: identity file /home/AsumomezaC-picoctf/.ssh/id_ed25519_sk type -1
debug1: identity file /home/AsumomezaC-picoctf/.ssh/id_ed25519_sk-cert type -1
debug1: identity file /home/AsumomezaC-picoctf/.ssh/id_xmss type -1
debug1: identity file /home/AsumomezaC-picoctf/.ssh/id_xmss-cert type -1
debug1: identity file /home/AsumomezaC-picoctf/.ssh/id_dsa type -1
debug1: identity file /home/AsumomezaC-picoctf/.ssh/id_dsa-cert type -1
debug1: Local version string SSH-2.0-OpenSSH_8.9p1 Ubuntu-3ubuntu0.10
debug1: Remote protocol version 2.0, remote software version OpenSSH_8.2p1 Ubuntu-4ubuntu0.8
debug1: compat_banner: match: OpenSSH_8.2p1 Ubuntu-4ubuntu0.8 pat OpenSSH* compat 0x04000000
debug2: fd 3 setting O_NONBLOCK
debug1: Authenticating to saturn.picoctf.net:64781 as 'picoplayer'
debug3: put_host_port: [saturn.picoctf.net]:64781
debug1: load_hostkeys: fopen /home/AsumomezaC-picoctf/.ssh/known_hosts2: No such file or directory
debug1: load_hostkeys: fopen /etc/ssh/ssh_known_hosts: No such file or directory
debug1: load_hostkeys: fopen /etc/ssh/ssh_known_hosts2: No such file or directory
debug3: order_hostkeyalgs: no algorithms matched; accept original
debug3: send packet: type 20
debug1: SSH2_MSG_KEXINIT sent
debug3: receive packet: type 20
debug1: SSH2_MSG_KEXINIT received
debug2: local client KEXINIT proposal
debug2: KEX algorithms: curve25519-sha256,curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,sntrup761x25519-sha512@openssh.com,diffie-hellman-group-exchange-sha256,diffie-hellman-group16-sha512,diffie-hellman-group18-sha512,diffie-hellman-group14-sha256,ext-info-c,kex-strict-c-v00@openssh.com
debug2: host key algorithms: ssh-ed25519-cert-v01@openssh.com,ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,sk-ssh-ed25519-cert-v01@openssh.com,sk-ecdsa-sha2-nistp256-cert-v01@openssh.com,rsa-sha2-512-cert-v01@openssh.com,rsa-sha2-256-cert-v01@openssh.com,ssh-ed25519,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,sk-ssh-ed25519@openssh.com,sk-ecdsa-sha2-nistp256@openssh.com,rsa-sha2-512,rsa-sha2-256
debug2: ciphers ctos: chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com
debug2: ciphers stoc: chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com
debug2: MACs ctos: umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-sha1
debug2: MACs stoc: umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-sha1
debug2: compression ctos: none,zlib@openssh.com,zlib
debug2: compression stoc: none,zlib@openssh.com,zlib
debug2: languages ctos: 
debug2: languages stoc: 
debug2: first_kex_follows 0 
debug2: reserved 0 
debug2: peer server KEXINIT proposal
debug2: KEX algorithms: curve25519-sha256,curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group16-sha512,diffie-hellman-group18-sha512,diffie-hellman-group14-sha256
debug2: host key algorithms: rsa-sha2-512,rsa-sha2-256,ssh-rsa,ecdsa-sha2-nistp256,ssh-ed25519
debug2: ciphers ctos: chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com
debug2: ciphers stoc: chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com
debug2: MACs ctos: umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-sha1
debug2: MACs stoc: umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-sha1
debug2: compression ctos: none,zlib@openssh.com
debug2: compression stoc: none,zlib@openssh.com
debug2: languages ctos: 
debug2: languages stoc: 
debug2: first_kex_follows 0 
debug2: reserved 0 
debug1: kex: algorithm: curve25519-sha256
debug1: kex: host key algorithm: ssh-ed25519
debug1: kex: server->client cipher: chacha20-poly1305@openssh.com MAC: <implicit> compression: none
debug1: kex: client->server cipher: chacha20-poly1305@openssh.com MAC: <implicit> compression: none
debug3: send packet: type 30
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug3: receive packet: type 31
debug1: SSH2_MSG_KEX_ECDH_REPLY received
debug1: Server host key: ssh-ed25519 SHA256:dMTscRrUiURy7uMu5eGWwEKdd2FzqLzx6LfWhssWnNQ
debug3: put_host_port: [13.59.203.175]:64781
debug3: put_host_port: [saturn.picoctf.net]:64781
debug1: load_hostkeys: fopen /home/AsumomezaC-picoctf/.ssh/known_hosts2: No such file or directory
debug1: load_hostkeys: fopen /etc/ssh/ssh_known_hosts: No such file or directory
debug1: load_hostkeys: fopen /etc/ssh/ssh_known_hosts2: No such file or directory
debug1: checking without port identifier
debug1: load_hostkeys: fopen /home/AsumomezaC-picoctf/.ssh/known_hosts2: No such file or directory
debug1: load_hostkeys: fopen /etc/ssh/ssh_known_hosts: No such file or directory
debug1: load_hostkeys: fopen /etc/ssh/ssh_known_hosts2: No such file or directory
debug3: hostkeys_find_by_key_hostfile: trying user hostfile "/home/AsumomezaC-picoctf/.ssh/known_hosts"
debug3: hostkeys_foreach: reading file "/home/AsumomezaC-picoctf/.ssh/known_hosts"
debug1: hostkeys_find_by_key_cb: found matching key in ~/.ssh/known_hosts:10
debug3: hostkeys_find_by_key_hostfile: trying user hostfile "/home/AsumomezaC-picoctf/.ssh/known_hosts2"
debug1: hostkeys_find_by_key_hostfile: hostkeys file /home/AsumomezaC-picoctf/.ssh/known_hosts2 does not exist
debug3: hostkeys_find_by_key_hostfile: trying system hostfile "/etc/ssh/ssh_known_hosts"
debug1: hostkeys_find_by_key_hostfile: hostkeys file /etc/ssh/ssh_known_hosts does not exist
debug3: hostkeys_find_by_key_hostfile: trying system hostfile "/etc/ssh/ssh_known_hosts2"
debug1: hostkeys_find_by_key_hostfile: hostkeys file /etc/ssh/ssh_known_hosts2 does not exist
The authenticity of host '[saturn.picoctf.net]:64781 ([13.59.203.175]:64781)' can't be established.
ED25519 key fingerprint is SHA256:dMTscRrUiURy7uMu5eGWwEKdd2FzqLzx6LfWhssWnNQ.
This host key is known by the following other names/addresses:
    ~/.ssh/known_hosts:10: [hashed name]
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '[saturn.picoctf.net]:64781' (ED25519) to the list of known hosts.
debug3: send packet: type 21
debug2: ssh_set_newkeys: mode 1
debug1: rekey out after 134217728 blocks
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug3: receive packet: type 21
debug1: SSH2_MSG_NEWKEYS received
debug2: ssh_set_newkeys: mode 0
debug1: rekey in after 134217728 blocks
debug1: Will attempt key: /home/AsumomezaC-picoctf/.ssh/id_rsa 
debug1: Will attempt key: /home/AsumomezaC-picoctf/.ssh/id_ecdsa 
debug1: Will attempt key: /home/AsumomezaC-picoctf/.ssh/id_ecdsa_sk 
debug1: Will attempt key: /home/AsumomezaC-picoctf/.ssh/id_ed25519 
debug1: Will attempt key: /home/AsumomezaC-picoctf/.ssh/id_ed25519_sk 
debug1: Will attempt key: /home/AsumomezaC-picoctf/.ssh/id_xmss 
debug1: Will attempt key: /home/AsumomezaC-picoctf/.ssh/id_dsa 
debug2: pubkey_prepare: done
debug3: send packet: type 5
debug3: receive packet: type 7
debug1: SSH2_MSG_EXT_INFO received
debug1: kex_input_ext_info: server-sig-algs=<ssh-ed25519,sk-ssh-ed25519@openssh.com,ssh-rsa,rsa-sha2-256,rsa-sha2-512,ssh-dss,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,sk-ecdsa-sha2-nistp256@openssh.com>
debug3: receive packet: type 6
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug3: send packet: type 50
debug3: receive packet: type 51
debug1: Authentications that can continue: publickey,password
debug3: start over, passed a different list publickey,password
debug3: preferred gssapi-with-mic,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /home/AsumomezaC-picoctf/.ssh/id_rsa
debug3: no such identity: /home/AsumomezaC-picoctf/.ssh/id_rsa: No such file or directory
debug1: Trying private key: /home/AsumomezaC-picoctf/.ssh/id_ecdsa
debug3: no such identity: /home/AsumomezaC-picoctf/.ssh/id_ecdsa: No such file or directory
debug1: Trying private key: /home/AsumomezaC-picoctf/.ssh/id_ecdsa_sk
debug3: no such identity: /home/AsumomezaC-picoctf/.ssh/id_ecdsa_sk: No such file or directory
debug1: Trying private key: /home/AsumomezaC-picoctf/.ssh/id_ed25519
debug3: no such identity: /home/AsumomezaC-picoctf/.ssh/id_ed25519: No such file or directory
debug1: Trying private key: /home/AsumomezaC-picoctf/.ssh/id_ed25519_sk
debug3: no such identity: /home/AsumomezaC-picoctf/.ssh/id_ed25519_sk: No such file or directory
debug1: Trying private key: /home/AsumomezaC-picoctf/.ssh/id_xmss
debug3: no such identity: /home/AsumomezaC-picoctf/.ssh/id_xmss: No such file or directory
debug1: Trying private key: /home/AsumomezaC-picoctf/.ssh/id_dsa
debug3: no such identity: /home/AsumomezaC-picoctf/.ssh/id_dsa: No such file or directory
debug2: we did not send a packet, disable method
debug3: authmethod_lookup password
debug3: remaining preferred: ,password
debug3: authmethod_is_enabled password
debug1: Next authentication method: password
picoplayer@saturn.picoctf.net's password: 
debug3: send packet: type 50
debug2: we sent a password packet, wait for reply
debug3: receive packet: type 52
Authenticated to saturn.picoctf.net ([13.59.203.175]:64781) using "password".
debug1: channel 0: new [client-session]
debug3: ssh_session2_open: channel_new: 0
debug2: channel 0: send open
debug3: send packet: type 90
debug1: Requesting no-more-sessions@openssh.com
debug3: send packet: type 80
debug1: Entering interactive session.
debug1: pledge: filesystem
debug3: receive packet: type 80
debug1: client_input_global_request: rtype hostkeys-00@openssh.com want_reply 0
debug3: client_input_hostkeys: received RSA key SHA256:wD1sbGdjbdCIe90J/vxPCMHOk4eTqUo4X4zSu71xD10
debug3: client_input_hostkeys: received ECDSA key SHA256:CB3YJzZNvPU4q/O98sAgEvAc2flYHI4go64WbfN3u54
debug3: client_input_hostkeys: received ED25519 key SHA256:dMTscRrUiURy7uMu5eGWwEKdd2FzqLzx6LfWhssWnNQ
debug3: put_host_port: [saturn.picoctf.net]:64781
debug1: client_input_hostkeys: searching /home/AsumomezaC-picoctf/.ssh/known_hosts for [saturn.picoctf.net]:64781 / (none)
debug3: hostkeys_foreach: reading file "/home/AsumomezaC-picoctf/.ssh/known_hosts"
debug3: hostkeys_find: found ssh-ed25519 key under different name/addr at /home/AsumomezaC-picoctf/.ssh/known_hosts:10
debug3: hostkeys_find: found ecdsa-sha2-nistp256 key under different name/addr at /home/AsumomezaC-picoctf/.ssh/known_hosts:11
debug3: hostkeys_find: found ssh-ed25519 key at /home/AsumomezaC-picoctf/.ssh/known_hosts:12
debug1: client_input_hostkeys: searching /home/AsumomezaC-picoctf/.ssh/known_hosts2 for [saturn.picoctf.net]:64781 / (none)
debug1: client_input_hostkeys: hostkeys file /home/AsumomezaC-picoctf/.ssh/known_hosts2 does not exist
debug3: client_input_hostkeys: 3 server keys: 2 new, 18446744073709551615 retained, 2 incomplete match. 0 to remove
debug1: client_input_hostkeys: host key found matching a different name/address, skipping UserKnownHostsFile update
debug3: receive packet: type 91
debug2: channel_input_open_confirmation: channel 0: callback start
debug2: fd 3 setting TCP_NODELAY
debug3: set_sock_tos: set socket 3 IP_TOS 0x10
debug2: client_session2_setup: id 0
debug2: channel 0: request pty-req confirm 1
debug3: send packet: type 98
debug1: Sending environment.
debug3: Ignored env SHELL
debug3: Ignored env LESS
debug3: Ignored env NVM_INC
debug3: Ignored env PWD
debug3: Ignored env LOGNAME
debug3: Ignored env HOME
debug3: Ignored env WINEPREFIX
debug3: Ignored env LS_COLORS
debug3: Ignored env NVM_DIR
debug3: Ignored env LESSCLOSE
debug3: Ignored env TERM
debug3: Ignored env LESSOPEN
debug3: Ignored env USER
debug3: Ignored env SHLVL
debug3: Ignored env NVM_CD_FLAGS
debug3: Ignored env WINEDEBUG
debug3: Ignored env TMOUT
debug3: Ignored env PATH
debug3: Ignored env NVM_BIN
debug3: Ignored env MAIL
debug3: Ignored env _
debug2: channel 0: request shell confirm 1
debug3: send packet: type 98
debug2: channel_input_open_confirmation: channel 0: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768
debug3: receive packet: type 99
debug2: channel_input_status_confirm: type 99 id 0
debug2: PTY allocation request accepted on channel 0
debug2: channel 0: rcvd adjust 2097152
debug3: receive packet: type 99
debug2: channel_input_status_confirm: type 99 id 0
debug2: shell request accepted on channel 0
Welcome to Ubuntu 20.04.5 LTS (GNU/Linux 6.5.0-1023-aws x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

This system has been minimized by removing packages and content that are
not required on a system that users do not log into.

To restore this content, you can run the 'unminimize' command.

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
```

Después usamos [[ls#Comando `ls -lath` en Linux]] para ver todos los detalles de los archivos del servidor.

```bash
picoplayer@challenge:~$ ls -lath
total 16K
drwxr-xr-x 1 picoplayer picoplayer   41 Feb 27 19:21 .
-rw------- 1 picoplayer picoplayer   22 Feb 27 19:21 .bash_history
drwx------ 2 picoplayer picoplayer   34 Feb 27 19:15 .cache
drwxr-xr-x 1 root       root         24 Aug  4  2023 ..
-rw-r--r-- 1 picoplayer picoplayer  220 Feb 25  2020 .bash_logout
-rw-r--r-- 1 picoplayer picoplayer 3.7K Feb 25  2020 .bashrc
-rw-r--r-- 1 picoplayer picoplayer  807 Feb 25  2020 .profile
```

Después usamos el comando [[pwd]] para verificar donde estamos trabajando.

```bash
picoplayer@challenge:~$ pwd
/home/picoplayer
```

Usamos [[crontab#3. Comandos útiles de `crontab`]] para ver que lista de tareas tenemos programadas.

```bash
picoplayer@challenge:~$ crontab -l
no crontab for picoplayer
```
>Nos damos cuenta que no tenemos ninguna tarea

Por lo cual usando [[CAT]] decidimos ver que contiene el archvio del sistema de [[crontab#6. Archivos de configuración de `cron`]].

```bash
picoplayer@challenge:~$ cat /etc/crontab
# picoCTF{Sch3DUL7NG_T45K3_L1NUX_7754e199}
```

Y obtenemos la bandera.
## Respuesta
picoCTF{Sch3DUL7NG_T45K3_L1NUX_7754e199}