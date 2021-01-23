
<h1>Syncro Ticket Creation</h1>

Syncro tickets can be created programmatically with the following script based on Magnus Box's job report functionality and the API.
Like other Syncro scripts, you will need to request an API account by emailing <a href="mailto:support@magnusbox.com">support@magnusbox.com</a>.
You can always contact us if you have any questions or run into problems.

** Disclaimer: Magnus Box did not write or develop this script, and the following configuration setup was developed by a Magnus Box partner. All rights
belong to their respective owner(s) **

<hr>

<h2>Setup</h2>

1. Download script from <a href="https://github.com/wellssd/comet-reporter">https://github.com/wellssd/comet-reporter</a>
1. Create custom asset field in Syncro titled "Comet Device ID" enter the device ID in this box. (Note: it needs to be the device ID and not the name). You can find it on <a href="https://drive.google.com/file/d/1cW6JRcM9ZA9iJtdAyuWMdtKWhuZXF7Pn/view?usp=sharing">this screenshot</a>.
1. Create new API key in Syncro. (Err on the side of more permissions since lesser permissions may cause issues. Exact requirements may be provided at a later date)
1. Edit script line #312 and fix the following:<br>
&nbsp; &nbsp;
<strike><code>if($(job.Status) -le 7009)</code></strike> should actually be <code>if(($job.Status) -le 7009)</code>

1. Edit the script, filling in the definitions on the top of the file, the CometPWD and CometUser name can be the same username/password that was created for you with the MagnusBox Syncro Integration Scripts.
1. Add the following to the top of the script to fix TLS errors:<br>
&nbsp; &nbsp;
<code>[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12</code>

<br><br>
<i>The script should be scheduled to run on a Windows machine that is always on, and the machine you have it on must have the Syncro Agent. You only need to run one copy of this script since it checks all of your clients.</i>
<br>
<i>Currently, the script does not work well with periodic backups and creates tickets erroneously for missed jobs. While we are working to solve this issue,
a solution may not become available for some time.</i>
