## Termux
```bash
termux-setup-storage
pkg up -y
pkg add proot-distro openssh tmux
pd install fedora

cat << EOF > .bashrc
#!/data/data/com.termux/files/usr/bin/bash

alias fedora="pd login fedora"

SSH_SERVER=true

if [ "$SSH_SERVER" = true ]; then
    if ! pgrep sshd > /dev/null 2>&1; then
        sshd &
    fi
    echo "SSH Running."
fi
echo "Type 'fedora' to enter Fedora"
EOF

echo "Set password for $(whoami): 123"
echo -e "123\n123" | passwd
```

## Fedora
```bash
dnf upgrade --refresh
dnf install git curl wget tmux
ln -s /data/data/com.termux/files/home /termux
```
