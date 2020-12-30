# Install Docker engine 
Follow the [link](https://docs.docker.com/engine/install/) install the docker engine

I used Ubuntu 18.04 version 

### Pull the docker image 
1. Cuda version
```
docker pull openfv/openfv-cuda
```
2. nonCuda version (CPU only)
```
docker pull openfv/openfv
```

### Check image tags and Create docker container based on the image
```
docker images
docker create -u root -it --name lf-cuda -p 8888:8888 -v $(pwd):/home/jovyan/work/liuhong_PIV 70aac7f7700e
docker start LF-Cuda
docker exec -it <container ID> bash
```

### Modify the jupyter notebook server configurration
```
cd ~/.jupyter
vi jupyter_notebook_config.py
 
```
add two lines into this config file to skip the password check
```
c.NotebookApp.token = ''
c.NotebookApp.password = u''
```
### Attach vscode host editor to container

Don't need to adjust the development container configuration file

### Modify the etc configure file to watch all files 

```
cd /etc
sudo vi sysctl.conf
```
add line
```
fs.inotify.max_user_watches=524288
```
save and quit

### TODO: synchronize with the dockhub