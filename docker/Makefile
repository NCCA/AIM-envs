# set user
user 			= 1000:0

# docker image and container details
Docker_name		= $(shell whoami)/aim-envs
container_name	= aim-envs

# forwards ports
ports 			= -p 8888:8888

# set volume directory
volume_dir 		= $(shell pwd):/workspace
dataset_dir		= /media/knoriy/DATA/Datasets/:/Datasets

build:
	@docker build . -t $(Docker_name)

run:
	@docker run -it --rm --gpus=all $(ports) -v $(volume_dir) -v $(dataset_dir) --name $(container_name) $(Docker_name)

lab:
	@docker run -it --rm --gpus=all $(ports) -e type=lab -v $(volume_dir) -v $(dataset_dir) --name $(container_name) $(Docker_name) || jupyter ${type} --ip 0.0.0.0 --no-browser --allow-root

bash:
	@docker run -it --rm --gpus=all $(ports) -v $(volume_dir) -v $(dataset_dir) --name $(container_name) $(Docker_name) bash || docker exec -it $(container_name) bash


