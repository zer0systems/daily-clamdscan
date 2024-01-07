# daily-clamdscan

![Virus Particle.](https://img.icons8.com/external-vitaliy-gorbachev-lineal-color-vitaly-gorbachev/100/external-virus-virus-transmission-vitaliy-gorbachev-lineal-color-vitaly-gorbachev-1.png)

## Daily ClamAV system scanning script (daily-clamdscan) v1.04

Baked for Debian-based distros...

### Overview:

Linux is a rather secure operating system, but it is not immune to malware attacks. Linux users should be aware of the common types of malware that can target their systems, such as rootkits, ransomware, and cryptominers. These malware can cause data loss, performance degradation, unauthorized access, and financial damage. To protect their systems from malware, Linux users should follow some best practices, such as keeping the system updated, using strong passwords, enabling two-factor authentication where available, using a VPN, and using antivirus software. Antivirus software can help detect and remove malware infections, as well as provide additional security features. This is where ClamAV comes in.

### Problem: 

Although ClamAV is an excellent malware scanner, it's not without its shortcomings. One of which this script attempts to tackle is ClamAV return codes. There currently exists three (3) available basic return codes for ClamAV. 

- Return code 0 = successful scan, no infections or errors
- Return code 1 = infection(s) detected
- Return code 2 = errors encountered

</ul>  

Depending on the execution of ClamAV and the order in which it encounters any infections and/or errors the final return code will always prevail. Therefore, if you have both infected files (return code 1) and errors (return code 2) this can result in either return code 1 or 2 depending the order in which ClamAV encounters them. This all but negates any proper return code interpretation and complicates scripting.

### Solution: 

This script aims to simply determine if a non-zero (1 and/or 2) return code is present after execution completes and notify (email) an administrator for further action, otherwise silently terminate. The alert email notification includes the ClamAV version, scan target(s), scan size, and a log attachment. Additionally, it provides log rotation. Finally, the script is FULLY customizable via variables.

### Deployment:

#### Requirements:

> [!IMPORTANT]
> The s-nail package is required for email attachments to fuction properly.

- The clamav package installed and provisioned
- A null mailer or MTA installed and configured
- The s-nail package installed

> [!TIP]
> The msmtp package is recommended as it is well maintained and constantly updated.

#### Setup:

1. Clone the repo to the desired directory:

<pre><code class="language-css">git clone https://github.com/zer0systems/daily-clamdscan.git</code></pre>

2. Change into the repo download directory and assign the script the proper permissions (enable execution):

<pre><code class="language-css">chmod 0775 daily-clamdscan</code></pre>

3. Symlink the script into you /etc/cron.daily directory:

<pre><code class="language-css">ln -s daily-clamdscan /etc/cron.daily/clamav</code></pre>

4. Customize the script via the variable definitions. Elements such as the directory(s) to be scanned (SCAN_DIR), monitoring recipient (MONITORING_EMAIL), log rotation interval (LOG_ROTATE), and more can all be configured as applicable.

### Future:

#### Possible upcoming features:

- Freshclam database update prior to scanning.

> [!NOTE]
> Feel completely free to suggest any future features you would like to see implemented. 😎
