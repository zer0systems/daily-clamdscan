# daily-clamdscan

<img width="100" height="100" src="https://img.icons8.com/external-vitaliy-gorbachev-lineal-color-vitaly-gorbachev/100/external-virus-virus-transmission-vitaliy-gorbachev-lineal-color-vitaly-gorbachev-1.png" alt="external-virus-virus-transmission-vitaliy-gorbachev-lineal-color-vitaly-gorbachev-1"/>

<h2>Daily ClamAV system scanning script (daily-clamdscan) v1.04</h2>

<p>Baked for Debian-based distros...</p>

<h3>Overview:</h3>

<p>Linux is a rather secure operating system, but it is not immune to malware attacks. Linux users should be aware of the common types of malware that can target their systems, such as rootkits, ransomware, and cryptominers. These malware can cause data loss, performance degradation, unauthorized access, and financial damage. To protect their systems from malware, Linux users should follow some best practices, such as keeping the system updated, using strong passwords, enabling two-factor authentication where available, using a VPN, and using antivirus software. Antivirus software can help detect and remove malware infections, as well as provide additional security features. This is where ClamAV comes in.</p>

<h3>Problem:</h3> 

<p>Although ClamAV is an excellent malware scanner, it's not without its shortcomings. One of which this script attempts to tackle is ClamAV return codes. There currently exists three (3) available basic return codes for ClamAV.</p> 

<ul>
  <li>Return code 0 = successful scan, no infections or errors</li>
  <li>Return code 1 = infection(s) detected</li>
  <li>Return code 2 = errors encountered</li>

</ul>  

<p>Depending on the execution of ClamAV and the order in which it encounters any infections and/or errors the final return code will always prevail. Therefore, if you have both infected files (return code 1) and errors (return code 2) this can result in either return code 1 or 2 depending the order in which ClamAV encounters them. This all but negates any proper return code interpretation and complicates scripting.</p>

<h3>Solution:</h3> 

<p>This script aims to simply determine if a non-zero (1 and/or 2) return code is present after execution completes and notify (email) an administrator for further action, otherwise silently terminate. The alert email notification includes the ClamAV version, scan target(s), scan size, and a log attachment. Additionally, it provides log rotation. Finally, the script is FULLY customizable via variables.</p>

<h3>Deployment:</h3>

<h4>Requirements:</h4>

<ul>
  <li>The clamav package installed w/ a basic configuration in place.</li>
  <li>The s-nail package installed (required for email attachment support).</li>
</ul>

<h4>Setup:</h4>

<p>Clone the repo:</p>

<pre><code class="language-css">git clone https://github.com/zer0systems/daily-clamdscan.git</code></pre>
