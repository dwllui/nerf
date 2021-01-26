Build the docker image for nerf (Tensorflow v2.41, CUDA 11 and cuDNN 8)
```
sudo docker build -t nerf-241 .
```

Otherwise, you can also pull the image down by
```
docker pull dennislui/nerf-241
```

Run the docker image with nvidia-docker2
```
# Replace <local_path_to_nerf_repo> accordingly
sudo docker run --runtime=nvidia -ti --rm -p 6006:6006 -v <local_path_to_nerf_repo>:/nerf --entrypoint /bin/bash nerf-241:latest
```

Once docker image is running navigate to the nerf folder and download the dataset (only required for the first time)
```
cd /nerf
bash download_example_data.sh
```

To start training a low res Fern NeRF:
```
python run_nerf.py --config config_fern.txt
```

In a different terminal on the local machine, start Tensorboard for the running container
```
# Find and replace <CONTAINER_ID> by running $ docker ps -a
sudo docker exec -it <CONTAINER_ID> bash
tensorboard --logdir=logs/summaries --host 0.0.0.0 --port 6006
```

Open browser on local machine and navigate to `http://localhost:6006`
