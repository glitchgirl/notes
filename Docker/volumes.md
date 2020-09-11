# volumes and bind mounts

- volumes make special location outside of containers UFS (universal flash storage)
    - Manual deletion
    -  Spec volume or we can add names with : (friendly name)
    - Used for setting up drivers, normally they have run cmd or setting it up in the dockerfile
- bind link container path to host path
    - Maps a host file or a directory to a conatiner of file/directory
    - Can't set up in dockerfile, must use run
