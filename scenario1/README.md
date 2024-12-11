# Combining base containers

To create a container that has both OpenFOAM and HPCToolkit installed:

```bash
# Prereqs
sudo add-apt-repository -y ppa:apptainer/ppa
sudo apt install -y apptainer
pip install ansible

# Get the mechanism's repo
git clone https://github.com/FoamScience/openfoam-apptainer-packaging /tmp/tainers
# then, from this folder:
ansible-playbook /tmp/tainers/build.yaml --extra-vars "original_dir=$PWD" --extra-vars "@config.yaml"

# From there, try:
apptainer run containers/basic/openfoam-hpctoolkit.sif blockMesh
apptainer run containers/basic/openfoam-hpctoolkit.sif hpcviewer
```
