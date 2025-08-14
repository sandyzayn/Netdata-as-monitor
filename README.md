# Netdata as Monitor

This project demonstrates how to quickly set up Netdata for system monitoring using Docker.

## Prerequisites
- Docker installed on your system
- Basic knowledge of command line usage

## Steps to Run Netdata

1. **Run the Netdata container:**
   
   Open a terminal and execute:
   
   ```sh
   docker run -d --name=netdata -p 19999:19999 --cap-add SYS_PTRACE --security-opt apparmor=unconfined \
     -v netdataconfig:/etc/netc/passwd:ro \
     -v /etc/group:/host/etc/group:ro \
     -v /proc:/host/proc:ro \
     -v /sys:/host/sys:ro \
     -v /etc/os-release:/host/etc/os-release:ro \
     netdata/netdata
   ```
   
   This command will pull the latest Netdata image and start the container with the required settings.

2. **Verify the container is running:**
   
   ```sh
   docker ps
   ```
   
   You should see a container named `netdata` in the list.

3. **Access the Netdata dashboard:**
   
   Open your browser and go to: [http://localhost:19999](http://localhost:19999)

## Files
- `run_netdata_docker_steps.txt`: Contains the Docker commands and explanations for quick reference.

## Notes
- Make sure the required ports and volumes are available and not used by other services.
- For more information, visit the [Netdata documentation](https://learn.netdata.cloud/docs/agent/packaging/docker/).

---

Feel free to modify the steps as per your environment or requirements.

## Example Screenshots

<img width="1919" height="1018" alt="Image" src="https://github.com/user-attachments/assets/9543f9f5-475b-4c12-b170-11f31a4b52e1" />

<img width="1919" height="1017" alt="Image" src="https://github.com/user-attachments/assets/f4c206f9-7f2c-4cf8-96e6-a11ccb9c8688" />

<img width="1919" height="1018" alt="Image" src="https://github.com/user-attachments/assets/b6eaa9ab-825b-4d7e-be50-4e0f1af64d22" />

<img width="1919" height="1017" alt="Image" src="https://github.com/user-attachments/assets/3460d595-9501-41eb-875c-f6d0a1148eb1" />

<img width="1919" height="1018" alt="Image" src="https://github.com/user-attachments/assets/e412a4ce-4d29-4573-910a-9c198c014559" />
