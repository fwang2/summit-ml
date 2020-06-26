# Machine Learning on Summit


```
module load ibm-wml-ce
18:52:44 $ conda create --name custom-wml --clone ibm-wml-ce-1.7.0-3
Source:      /sw/summit/ibm-wml-ce/anaconda-base/envs/ibm-wml-ce-1.7.0-3
Destination: /ccs/home/fwang2/.conda/envs/custom-wml
```

The details on loaded module can be found at [olcf user doc](https://docs.olcf.ornl.gov/software/analytics/ibm-wml-ce.html), the 1.7.0 release has package information on [ibm site](https://www.ibm.com/support/knowledgecenter/SS5SF7_1.7.0/navigation/wmlce_software_pkgs.html) as well.


## Connect to 

```
# first step: to login node
ssh -L8888:localhost:8000 -X -I /usr/local/lib/opensc-pkcs11.so fwang2@summit.olcf.ornl.gov
# second step: to batch node (after node request granted)
bsub -P STF008 -nnodes 1 -W 60 -alloc_flags gpumps -Is /bin/bash
# 3rd step: onto compute node, echo $LSB_HOSTS will tell you the hostname
ssh -L 8000:localhost:8887 b25n14
```
