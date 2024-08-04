### Configure Resources

Once you have logged into your node, run:
```bash
sudo apt update
sudo apt-get install -y ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc
echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt update
sudo apt-get install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```
to install Docker.

You can verify that the Docker Engine installation was successful by running the hello-world image:
```bash
sudo docker run hello-world
```
If the installation is working correctly you should see:
```
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
c1ec31eb5944: Pull complete
Digest: sha256:1408fec50309afee38f3535383f5b09419e6dc0925bc69891e79d84cc4cdcec6
Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.
```

To pull the docker image used in the experiment from Docker Hub run
```bash
sudo docker pull shanist/dnssim:1.7
```

We will use tshark to view network packet captures. Run:
```bash
sudo apt-get install -y tshark
```
to install tshark on your node. By viewing the captures, we can see the resolution route of queries.

The docker environment has Valgrind's callgrind tool pre-installed. This tool records the call history among functions and will be used to record the number of instructions executed on the r on the resolver during queries. We will use the KCachegrind tool for viewing the results files generated by callgrind. Run:
```bash
sudo apt-get install -y kcachegrind
```
to install KCachegrind.

When you have finished installing the necessary software dependencies, continue to the next section to verify your setup.