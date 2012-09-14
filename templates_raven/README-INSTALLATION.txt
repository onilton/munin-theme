#################################
## RAVEN TEMPLATES FOR MUNIN

This file explains what Raven the raven theme/templates are and how you can use them on your Munin installation. 

Version: 0.1 - Feb 17 2011
Author: Jeremy Clarke
Author URL: http://jeremyclarke.org
License: GPL, based on descendence from the Munin core. See FSF website for details:
http://www.gnu.org/licenses/gpl.txt

More info: http://jeremyclarke.org/?s=munin

#################################
## WHAT IS RAVEN?

Raven is a set of templates you can use in your Munin installation to give it a different look and add javascript-based tabs on the overview page. 

Munin makes it easy to modify the template files that generate the HTML of the reports, but there are not many themes out there, which is why I am releasing this one to the public.

Raven will not affect the functioning of your Munin "nodes" (the part that actually monitors servers). You only have to install it on your Munin "master" for it to affect the HTML and style of all your reports. 

#################################
## FEATURES

* Javascript-enabled to replace neverending overview page with a tabbed box to organize the various reports.
* Nicer CSS with larger text, tighter spacing and soft, pleasant colors.
* Less ugly!

#################################
## INSTALLATION

There are two ways to install a custom theme in Munin: The clean way using munin.conf and the messy way by replacing all files in the default template directory.

#################################
## INSTALLING THE CLEAN WAY WITH munin.conf AND htmldir

The safest and cleanest way to install Raven is to upload the templates into a new directory in your Munin configuration folder, then change your munin.conf file to tell it to use the new template directory instead of the default. You also need to upload a directory into your "htmldir".

This process is designed to leave the default files alone and not overwrite them, it should be easily reversible by changing your 'htmldir' property in munin.conf back to the default.

Follow the steps below:

SHORT VERSION - All steps apply to Munin "master" only

	* Upload the "templates_raven" directory from this zip file into your Munin config directory (i.e. same directory that munin.conf is in, probably /etc/munin/)
	
	* Upload the 'raven-htmldir-files' directory from this zip file into your Munin HTML directory (where the public HTML is served from).
	
	* Edit your "munin.conf" file on the master and change the "tmpldir" property to reference the new "templates_raven" directory in your Munin config directory instead of the default "templates".
	
	* Wait 5 minutes for the Munin master to refresh itself and reload. 
	
	
LONG VERSION - All steps apply to the Munin "master" only

	* Find your Munin configuration directory. This is the directory that contains your munin.conf file as well as plugins and templates. It is probably in /etc/munin/ though it may be somewhere else depending on your setup. 
	
	* Upload the "templates_raven" directory from this zip file into the Munin configuration folder. It should end up in the same place as the pre-existing "templates" directory, which contains the default Munin HTML templates.
		
	* In the munin.conf file (where you set up your node servers during initial configuration) find the "tmpldir" property. It should be near the top, under a comment saying "Where to look for the HTML templates". 
	
	* Comment out the "tmpldir" property and replace it with a new one that points to "templates_raven" instead of "templates". Here's how it should look afterwards:

---IN YOUR MUNIN.CONF FILE---

# Where to look for the HTML templates
#tmpldir	/etc/munin/templates
tmpldir	/etc/munin/templates_raven

---END MUNIN.CONF EXAMPLE---

	* Next you need to find your "htmldir", this is the directory that Munin saves the output HTML files to. It is the same place you set up in Apache or other webserver during your initial Munin setup. 
	
	* The easiest way to find the "htmldir" is to look for the "htmldir" property in your munin.conf file that we edited earlier. When you find the directory it should contain the HTML files output by Munin like "definitions.html" and "style.css"
	
	* Upload the entire "raven-htmldir-files" directory into "htmldir". This means the directory itself should be there, as well as the files inside. 
	
	* That's it! Wait 5 minutes for the Munin master to refresh itself (which reloads the HTML using our new templates) and check your reports to make sure they are using the Raven styles.
	
#################################
## INSTALLING THE MESSY WAY BY RENAMING DIRECTORIES

This method IS NOT RECOMMENDED because it may not be futureproof and can easily lead to problems. Renaming directories is error prone and you might lose the default files and not be able to get them back without re-installing Munin.

This method should only be used if you can't access the munin.conf file for some reason, which shouldn't happen. 

	* See instructions above for finding your Munin configuration directory (probably /etc/munin/ ) and "htmldir" directory where the final reports are stored. 

	* In your Munin configuration directory rename "templates" to "templates_default_backup", this way we don't lose the defaults in case there is a problem. Renaming this directory back to "templates" should bring you back to the standard Munin theme if you have any problems.

	* Create a new "templates" directory and upload into it the contents of the "templates_raven" directory from this zip file. 

	* Go to your "htmldir" and upload the entire "raven-htmldir-files" direcory (both the directory and the files).

	* Wait 5 minutes for the Munin master to reload then check to make sure Raven is being used. 
	
