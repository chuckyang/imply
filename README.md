Dockerized version of the distribution available at https://imply.io/download.

[Install Docker](docker-install.md)

To build an image, first download the Imply distribution from the link above, place it in the cloned repository, and then run:

```
export implyversion=2.4.8
tar -xzf imply-$implyversion.tar.gz
docker build -t imply:$implyversion --build-arg implyversion=$implyversion .
```

To run the image in quickstart mode (single-machine, non-clustered):

```
sudo docker run --mount type=bind,source=$(pwd)/data,target=/opt/imply-2.4.8 -p 8081-8110:8081-8110 -p 8200:8200 -p 9095:9095 -d --name imply jybaby1027/imply-office
```

To load the example data:

```
docker exec -it imply bin/post-index-task -f quickstart/wikiticker-index.json
```

To enter the container, if you want:

```
docker exec -it imply /bin/bash
```

To stop the container:

```
docker stop imply
```
