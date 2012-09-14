munin-theme
===========
It's [Raven's custom theme](http://simianuprising.com/2011/02/19/raven-my-custom-theme-templates-for-munin/)
 working for munin 1.4.6. There a some pieces that I took from [Shauna great update](http://blog.shaunagordon.com/2011/04/jeremy-clarke-made-nice-sleek.html) for 1.4.4 .

I started this one mostly because of the broken comparison views. But maybe in the future I will put [Twitter's boostrap](http://twitter.github.com/bootstrap/) in the theme. :P Who nows?

Main changes:

* Updated auto-refresh (older interval was annoying)
* Comparison views working (and with tabs)

##Install

###Manual

####Dowload

Download with git

git clone https://github.com/oniltonmaciel/munin-theme.git

You can also download github zip (it's up there next to the HTTP|SSH button)

Now enter the dir

	$ cd munin-theme


####templates_raven
	
Copy templates_raven to munin config folder

	$ cp -r templates_raven /etc/munin/

Update munin config to point to the our new templates folder. Open the file in your favorite editor

	$ gedit /etc/munin/munin.conf

Look for this line

	# tmpldir       /etc/munin/template

And change so the lines should be like this

	# tmpldir       /etc/munin/template
	tmpldir       /etc/munin/templates_raven

####raven-htmldir-files

Discover where is your Munin HTML directory

	$ cat /etc/munin/munin.conf | grep "^#\ *htmldir" | grep -o "/.*"


Or look for `htmldir` in your `/etc/munin/munin.conf` file just to confirm

In Ubuntu, it should be 

	/var/cache/munin/www

Copy `raven-html-dir-files` to your munin HTML directory

The command in Ubuntu is

	cp -r raven-html-dir-files /var/cache/munin/www

###Wait

You will probably will have to wait up to 5 minutes after this changes. Be patient! =D
