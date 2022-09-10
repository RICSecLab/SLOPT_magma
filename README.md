# Magma for SLOPT

This is a repository forked from the original [Magma](https://github.com/HexHive/magma).
MAGMA is a ground- truth fuzzing benchmark in real-world software; 
bugs are inserted artificially and each crash triggered by a fuzzer can be identified.
Please refer [their document](https://hexhive.epfl.ch/magma/) for the detail of this benchmark itself.
Especially, [Getting Started](https://hexhive.epfl.ch/magma/docs/getting-started.html) is helpful
if you are not familiar with Magma.

Here, we explain how to execute the experiment.

### Requirements

If you are using Ubuntu, then you can install the required packages as follows.
```
apt-get update &&
  apt-get install -y util-linux inotify-tools docker.io git
```

Note that your user is expected to be able to execute `docker` without sudo.

### captainrc

`captainrc` is a confiuration file for Magma experiments.
You can adjust the experimental setting to your environment (e.g. number of proccesses that run parallelly.)
Parameters are not changed compared with the original Magma;
therefore you can refer the original doc if you want to change some of them.

Note that `slopt` is our fuzzer's name. 
Therefore, please make sure that `FUZZERS` and `slopt_TARGETS` are set correctly.
We put two `captainrc` files which we used during our experiments for your information at the root of this project

### Start Magma experiment

After you finish configurating captainrc, you can execute your Magma experiment just by `./tools/captain/run.sh`.


### After your experiment

Let `slopt-magma` be your working directory configured in your captainrc (like `WORKDIR=./slopt-magma`).
You can summarize the result by `tools/benchd/exp2json.py slopt-magma slopt-magma.json`.
The generated json file contains which bug is reached and which bug is triggered.


