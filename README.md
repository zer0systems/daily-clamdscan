# daily-clamdscan

<h2>Daily ClamAV system scanning script (daily-clamdscan) v1.01</h2>

<h3>Overview:</h3> 

There currently exists three (3) available basic return codes for ClamAV. Return code 0 = success, return code 1 = infection(s), and return code 2 = errors. Depending on the execution of ClamAV and the order in which it encounters any infections and/or errors the final return code will always prevail. Therefore, if you have both infected files (return code 1) and errors (return code 2) this can result in either return code 1 or 2 depending the order in which ClamAV encounters them. This all but negates any proper return code interpretation and complicates any scripting with odd logic.

<h3>Purpose:</h3> 

This script aims to simply determine if a non-zero (1 and/or 2) return code is present after execution and notify (email) an administrator for further action, otherwise silently terminate. All of the needed variable definitions can be updated occordingly as applicable. The alert email notification includes the ClamAV version, scan target(s), scan size, and a log attachment. You can additionally control the log rotation interval.

<h3>Deployment:</h3>
<i>Coming soon...</i>
