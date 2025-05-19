# 🔐 Ansible Fail2Ban Log Analyzer

This Ansible playbook 📘 automates the task of extracting, counting, and saving banned IPs from the **Fail2Ban** log file on remote hosts. It helps security teams quickly gather data within a specified time window and generate detailed reports locally for further analysis. 📊

---

## 📁 Project Structure

```
.
├── tasks/
│   └── main.yml
├── vars/
│   └── main.yml
├── handlers/
│   └── main.yml
└── reports/
    └── fail2ban-cdn/
```

---

## 🚀 Features

✅ Count banned IPs between a specified time range  
✅ Save all matching logs into timestamped files  
✅ Fetch generated logs from remote servers to the Ansible controller  
✅ Output results for visibility during execution  

---

## 🧾 Variables

Defined in `vars/main.yml`:

```yaml
start_time: "2025-05-10 11:00:00"  # Define start time
end_time: "2025-05-11 13:00:00"    # Define end time
```

Adjust these values to filter logs for your desired time range.

---

## ⚙️ Tasks Overview (`main.yml`)

| Step | Description |
|------|-------------|
| 🔍 **Count banned IPs** | Counts entries with `Ban` between `start_time` and `end_time`. |
| 📢 **Show count** | Displays the number of banned IPs found. |
| 📜 **Extract logs** | Filters `fail2ban.log` for `Ban` entries within the specified time range. |
| 📂 **Create directory** | Ensures `/home/ansible/fail2ban-cdn` exists on the remote host. |
| 💾 **Save file** | Saves filtered logs to a timestamped file on the remote host. |
| 📥 **Fetch file** | Copies the file back to the Ansible controller into `./reports/fail2ban-cdn/`. |
| 🧾 **Show entries** | Prints each banned IP entry for review. |

---

## 🧪 Example Run

```bash
ansible-playbook -i inventory playbook.yml
```

Upon successful execution, a file like the following will appear in your `reports/fail2ban-cdn/` directory:

```
reports/fail2ban-cdn/webserver1_2025-05-11_13:22:01_banned_ips.txt
```

---

## 📌 Notes

- Make sure `fail2ban.log` is available at `/var/log/fail2ban.log` on your target hosts.
- Ensure the Ansible user has read permissions on the log file.
- Ansible controller should have permission to write to the `./reports/fail2ban-cdn/` directory.

---

## 🛡️ License

MIT License © 2025

---

## 🤝 Contributions

PRs are welcome! If you have improvements, ideas, or bug fixes, feel free to open an issue or submit a pull request. 🚀

---

✨ Author
Milad Vahdatkhah – DevOps & Automation Enthusiast 💻🛠️
