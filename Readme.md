### What is NCI
Read this:

https://nci.org.au/

### {} steps for starting to use NCI

#### Step 1 Signup

You should register for a new NCI account 

https://my.nci.org.au/mancini/signup/0

You should get a username after providing your information, the username should be consisted of two lower case characters and four numbers.

#### Step 2 Login

Login by using mobaxterm or wsl on window11 (VPN free) 

```
ssh {username}@gadi.nci.org.au
```

#### Step 3 Set up your home 

Each user only have 1 gb space in their home folder, so install a miniconda

https://docs.conda.io/en/latest/miniconda.html

```
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh

bash Miniconda3-latest-Linux-x86_64.sh
```

Make your own folder in gdata

```
mkdir -p /g/data/{your project id}/{your user name}
```

##### About storage

Gadi has two places to store files, gdata and scratch, available space of /gdata is 3TB, /scratch is 1TB. In principle, files stored in /scratch 


You can check space already used by your project:

```
nci_account -P {your project id}
```

Check how much space does each user in your project used:

scratch :

```
nci-files-report -f scratch --group {your project id}
```

gdata:

```
nci-files-report -f gdata --group {your project id}
```

You may notice when you use 'nci_account -P' to check space already used, you can also get a usage report.

I personally regard KSU as a type of currency, the more you used, the more you will be charged.

For example:

Usage Report: Project={} Period=2021.q4 <-----q4 means the 4th quarter
    Grant:    75.00 KSU     <----- total ksu in each quarter
     Used:    40.34 KSU     <----- ksu you have used in this quarter
 Reserved:     0.00 SU
    Avail:    34.66 KSU     <----- ksu you can use in this quarter

You can check how they charge compute jobs: 
https://opus.nci.org.au/display/Help/2.+Compute+Grant+and+Job+Debiting

How different types of job queue cost:

https://opus.nci.org.au/display/Help/2.2+Job+Cost+Examples

Use normal queue in most situations. 

#### Step 4 









#### Some tips 

### About Singularity 


