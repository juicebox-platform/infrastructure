# infrastructure

## env
```bash
uv sync
source .venv/bin/activate
ansible-galaxy collection install git+https://github.com/k3s-io/k3s-ansible.git
```

## vault
```bash
ansible-vault create secrets.yml
```

```bash
uv run ansible-playbook site.yml -i production --extra-vars
 "@secrets.yml" --vault-password-file .vault_password
```


## tls-san
```bash
sudo vim /etc/systemd/system/k3s.service

# append this to the ExecStart line:
--tls-san juicebox.com

sudo systemctl daemon-reload
sudo systemctl restart k3s
```

