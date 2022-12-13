# Slurm plugin development environment for OpenStack

The repository contains scripts for creating a temporary development environment for developing extensions for Slurm batch scheduler. It’s rather impossible to easily modify the configuration of the production
deployment without affecting other users of HPC systems. Therefore, I created a script to automate
the HPC development environment on OpenStack. The main advantage of using the OpenStack is,
that it can effortlessly stop or update our cluster stack. I used the Heat Orchestration Templates
(HOT) to describe the OpenStack architecture and the Ansible automation tool for installation and
configuration. The installation and configuration supports the CentOS 8 Stream, but can be quite
simply adapted for other operating systems supported by the Slurm (batch scheduler).

Read the [`article`](https://github.com/io-sea/slurm-openstack-devel-plugin/blob/main/2022-PPFIT-SlurmOpenStackPluginDevel.pdf) for more information.

Installation can be watched by `tail -f /var/log/cloud-init-output.log` in master node.
User, who would like to e.g. `sbatch` executable or script, should be in the `slurm` group. JWT token can be obtained by `scontrol token username=<username>` as superuser.

## Acknowledgement
This work was supported by the IO-SEA project. This project has received funding from the European High-Performance Computing Joint Undertaking (JU) under grant agreement No 955811. The JU receives support from the European Union’s Horizon 2020 research and innovation programme and France, Germany, the United Kingdom, Ireland, the Czech Republic, Sweden. This project has received funding from the Ministry of Education, Youth and Sports of the Czech Republic (ID: MC2105).


## Structure
```
 |- old_scripts -- contains scripts, which helped me to develop the automation script.
 |- openstack_init
    |- ansible -- ansible playbook and roles
    |- files -- like configuration files for slurm
    |- scripts -- python scripts used while installation
    |- slurm_services -- systemV services used while setting up Slurm

```

# Tested images
- CentOS-7
- CentOS-Stream-8_20210210
