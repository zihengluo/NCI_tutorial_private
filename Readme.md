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

You can check your home space by using:

```
quota -s -f /home
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

You can also use this:

```
lquota
```

You may notice when you use 'nci_account -P' to check space already used, you can also get a usage report.

I personally regard KSU as a type of currency, the more you used, the more you will be charged.

For example:

----------------------------------------------------------------------
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

#### Step 4 Write a script for submitting PBS job






#### Step 5 Submit your job




#### Step 6








------------------------------------------------------------------------------
#### Some tips 




#### What should I do if my home is full but I still need to create a new conda environment

You can remove some environments you no longer need. You can run this to save these environment settings and create new environments with these config files when you need them.

```

```


Or

you can create conda environment in another directory (not quite recommend)

For example

```
conda create --prefix {to/the/folder/you/like}

conda activate {to/the/folder/you/like}

```

Files will save in 



#### Why my job not run (both submitting job and interactive job)



#### How to transfer files between remote servers or local computer



#### Why I can't transfer large files to NCI

Non-interactive job will be killed after 30 minutes, to transfer large files, you can submit a PBS job for transfering.   



####



#### About Singularity 

NCI not allow user to make writable singularity container by using fake-root or sandbox, you can't use mysql.

Singularity image can be big, some files will automatelly save in ./singularity (your home path), which may make you get a error like:

WARNING: mkdir {xxxx}/.singularity: disk quota exceeded

To avoid this error, you can create a folder in scratch then link this folder to the .singularity folder in your home path

```
mkdir -p /scratch/{your project id}/{your username}/.singularity

ln -s /scratch/{your project id}/{your username}/.singularity ${HOME}/.singularity
```

Then you should be able to download singularity image by using 'singularity pull'
