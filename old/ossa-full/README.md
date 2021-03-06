# ossa-full.sh
<img width=600 src="https://raw.githubusercontent.com/ThinGuy/svg/master/ossa-full.png?sanitize=true" title="ossa-full.sh -Sk">
This script should be run from the system that is being assessed

## Script Duration
ossa-full.sh should complete is less than 5 minutes, but will usually finish much quicker on modern systems.

## Script Options
* Get script options by running the following:

	```
	./ossa-full.sh -h
	```

* Help options will be displayed

``` 
 Script: ossa.sh

 Usage: ossa.sh [ Options ] 

 Options:

   -d, --dir               Directory to store Open Source Security Assessment Data (Default: /tmp/ossa_files)

   -s, --suffix            Append given suffix to collected files (Default: ".orangebox20.orangebox.me.focal"

   -o, --override          Do perform password scrubbing of embedded credentials (Default: false)

   -n, --no-purge          Do NOT purge existing OSSA Directory (Default: False)

   -k, --keep              Keep OSSA Directory after script completes (Default: False)

   -e, --encrypt           Encrypt OSSA Datafiles with given passphrase (Default: False)

   -m, --no-madison        Do not run apt-cache madison against package manifest (Default: False)

   -O, --origins           If you are running a mirror of an official ubuntu repository,
                           add the URL(s) to they can be marked as official

                           Note: Format should be a single URL or a space/comma
                                 separated list, surrounded by quotes

   -S, --scan              Install OpenSCAP & scan manifest for CVEs. Sudo access is required only
                           if OpenSCAP is not installed. (Default: False)

   -h, --help              This message

 Examples:

   Change location of collected data:
     ./ossa-full.sh -d $HOME/ossa_files

   Set custom file suffix:
     ./ossa-full.sh -s dc1.psql001.xenial

   Perform CVE Scan, encrypt compressed archive of collected data, and
     keep data directory after run

     ./ossa-full.sh -Ske 'MyP@ssW0rd!' 
```


### Transfer Script to Remote Machine
Your current working directory must be in ossa/ossa-full, where this file
is located. Once in ossa/ossa-full you can:

* Transfer the script a remote system using scp:

	```
	scp ossa-full.sh user@host:.
	```

### Run Script on  Remote Machine

* ssh to remote machine:

	```
	ssh user@host
	```

* Get list of script options:

	```
	./ossa-full.sh -h
	```

* Run script using desired options:

	```
	./ossa-full.sh -Spke 'MyP@55w0rD123!'
	```

### Transfer Results to your machine
Once ossa-full.sh has completed, you may want to collect the data from the machine.
* The name and path of the archive will be presented once the script has completed:

	```
	 Open Source Security Assessment completed in 00:01:43

	 Encrypted data collected during the Open Source Security Assessment is located at
	 /tmp/ossa-datafile.encrypted.orangebox20.focal.tgz
	```

* Download the script output using scp:

	```
	scp user@host:/tmp/ossa-datafile.encrypted.orangebox20.focal.tgz .
	```
