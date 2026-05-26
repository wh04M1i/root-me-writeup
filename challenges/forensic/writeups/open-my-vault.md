## Challenge name: Open My Vault

```Challenge Link:``` [https://www.root-me.org/en/Challenges/Forensic/Open-My-Vault](https://www.root-me.org/en/Challenges/Forensic/Open-My-Vault)

**Ansible vault password recovery from log analysis.**

### Step 1: Examine user history

After SSHing into the server, check the bash history of the user:

```bash
history
```

The history shows that user `m4st3r` ran an Ansible playbook with a vault password stored at `/tmp/.secure`, then deleted it:

```bash
ansible-playbook -i inventory.cfg --vault-password-file=/tmp/.secure playbook.yml
rm /tmp/.secure
```

### Step 2: Check Apache logs

Check `/var/log/apache2/access.log` for clues:

```bash
tail -f /var/log/apache2/access.log
```

Found a command injection in the logs:

```
203.0.113.0 - - [03/Sep/2022:13:34:31 +0200] "GET /pdf.php?name=a.pdf;echo%20%22C4tXk9ctpG9QEMeL%22%20%3E%20/tmp/.secure HTTP/1.1" 200 31
```

URL-decoded:
```
echo "C4tXk9ctpG9QEMeL" > /tmp/.secure
```

### Step 3: Decrypt the vault

Use the recovered password to decrypt the Ansible vault:

```bash
echo "C4tXk9ctpG9QEMeL" > /tmp/.secure
ansible-vault decrypt --vault-pass-file /tmp/.secure roles/other/tasks/main.yml
```

The decrypted playbook reveals the flag.
