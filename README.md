# Machine Learning on Summit


```
module load ibm-wml-ce
18:52:44 $ conda create --name custom-wml --clone ibm-wml-ce-1.7.0-3
Source:      /sw/summit/ibm-wml-ce/anaconda-base/envs/ibm-wml-ce-1.7.0-3
Destination: /ccs/home/fwang2/.conda/envs/custom-wml
```

The details on loaded module can be found at [olcf user doc](https://docs.olcf.ornl.gov/software/analytics/ibm-wml-ce.html), the 1.7.0 release has package information on [ibm site](https://www.ibm.com/support/knowledgecenter/SS5SF7_1.7.0/navigation/wmlce_software_pkgs.html) as well.


## Connect to 

### step 1: to login node
```
ssh -X -I /usr/local/lib/opensc-pkcs11.so fwang2@summit.olcf.ornl.gov
```

### step 2: to batch node (after node request granted)
```
bsub -P STF008 -nnodes 1 -W 60 -alloc_flags nvme -Is /bin/bash
```

### step 3: to ~/distributed-learning-summit
```
jsrun -n1 -a1 -c42 -g6 -r1 ./jupyterlab/compute.sh 8887
```

The most important information after this is:

```
The Jupyter Notebook is running at
http://h36n04:8887/
```


# final step:


```
ssh  -L9999:localhost:8000 -X -I /usr/local/lib/opensc-pkcs11.so fwang2@summit.olcf.ornl.gov
ssh -L 8000:localhost:8887 b36n04
```
