# ubuntu_itcar
Ubuntu command setups for IT_Car

//Nvidia driver
    1  nvidia-smi
    2  ubuntu-drivers devices
    3  nvidia-driver-535
    4  sudo ubuntu-drivers autoinstall
    5  nvidia-smi
    6  sudo reboot

//docker
Docker là một phần mềm nguồn mở được thiết kế để hỗ trợ và đơn giản hóa việc phát triển ứng dụng. Nó là một tập hợp các platform-as-a-service products tạo ra các virtualized environments cô lập để building, deploy , và testing các ứng dụng.
Docker image là một file bất biến - không thay đổi, chứa các source code, libraries, dependencies, tools và các files khác cần thiết cho một ứng dụng để chạy.
Docker container là một run-time environment mà ở đó người dùng có thể chạy một ứng dụng độc lập. 

   27  sudo apt update
   28  sudo apt install apt-transport-https ca-certificates curl software-properties-common
   29  curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
   30  sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"
   31  apt-cache policy docker-ce
   32  sudo apt install docker-ce
   33  sudo systemctl status docker
   
   //add user
   34  sudo usermod -aG docker ceec_member
   35  su - ceec_member
   36  groups
   maybe sudo reboot
   //testing
   docker run hello-world

//nvidia container toolkit
   39  curl -fsSL https://nvidia.github.io/libnvidia-container/gpgkey | sudo gpg --dearmor -o /usr/share/keyrings/nvidia-container-toolkit-keyring.gpg   && curl -s -L https://nvidia.github.io/libnvidia-container/stable/deb/nvidia-container-toolkit.list |     sed 's#deb https://#deb [signed-by=/usr/share/keyrings/nvidia-container-toolkit-keyring.gpg] https://#g' |     sudo tee /etc/apt/sources.list.d/nvidia-container-toolkit.list   &&     sudo apt-get update
   40  sudo apt-get install -y nvidia-container-toolkit

//setups+docker_tutor
https://drive.google.com/file/d/1On6iAmioqvXPbQl20_R3ndLwDB5msQj9/view?usp=drivesdk
https://docs.google.com/document/d/1jeUR6GjCre7cgNVibWkCL3-wlsYhwPEh/edit
   41  docker pull quocle28/it_car_2023:v1
   42  xhost +local:docker
   20  docker image ls
   22  docker run --name it-car -it -p 11000:11000 --network="host"  -e DISPLAY=$DISPLAY -v /tmp/.X11-unix:/tmp/.X11-unix --gpus all "imageid"
   // Command run on server: sudo docker run -itd --name nghiatg --gpus all --shm-size="24g" --mount type=bind,source=/home,target=/home nvidia/cuda:12.2.0-devel-ubuntu20.04
//Download visualcode
https://code.visualstudio.com/docs/setup/linux (chon download)
   45  cd Downloads/
   46  sudo dpkg -i code_1.83.1-1696982868_amd64.deb 
   
--> cai extension docker vs dev contrainer
NOTE:
client_lib: thu vien giao tiep code python voi unity
test_client: minh hoa cach su dung de tuong tac unity
getstatus: vi tri cua xe 
getraw: anh raw tu camera (anh mau`)
getseg: anh segment tu raw
--> Luu y the le nam nay
AVcontrol gui toc do va goc lai de dieu khien xe

show 1 so thu vien ban to chuc cai san, cv2, pytorch
chay xong thi stop, start tren visual luon
cai` them thu vien thi nho commit
63  docker commit "containerid" ceec_member/it_car_2023:v1
64  docker image ls
65  docker save -o ceec_member_itcar2023.tar ceec_member/it_car_2023:v1
66  ls
67  docker image rm "imageid"
69  docker load --input tri_itcar2023.tar
72  docker run --name it-car1 -it -p 11000:11000 --network="host"  -e DISPLAY=$DISPLAY -v /tmp/.X11-unix:/tmp/.X11-unix --gpus all "newimageid"
73  docker image ls

sudo nvidia-smi -pm 1 --> Turn on GPU in nvidia-smi

 
