
---

# Netdata as Monitor

This project demonstrates how to quickly set up **Netdata** for real-time system monitoring using Docker.
Netdata provides a comprehensive and interactive dashboard for tracking CPU, memory, disk, network, and many other system metrics.

---

---

## 💡 Introduction

Netdata is an open-source monitoring agent designed for performance and health monitoring of systems and applications.
This guide walks you through setting it up inside a Docker container for quick deployment and easy access to its dashboard.

---

## ✅ Prerequisites

Before starting, ensure you have:

* **Docker** installed and running on your system
* **Basic command-line knowledge**
* Port **19999** available for the dashboard
* Sufficient permissions to mount host system files into the container

---

## 🚀 Installation & Running

### 1. Run the Netdata container

In your terminal, execute:

```sh
docker run -d --name=netdata -p 19999:19999 --cap-add SYS_PTRACE --security-opt apparmor=unconfined \
  -v netdataconfig:/etc/netdata \
  -v netdatalib:/var/lib/netdata \
  -v netdatacache:/var/cache/netdata \
  -v /etc/passwd:/host/etc/passwd:ro \
  -v /etc/group:/host/etc/group:ro \
  -v /proc:/host/proc:ro \
  -v /sys:/host/sys:ro \
  -v /etc/os-release:/host/etc/os-release:ro \
  netdata/netdata
```

This will:

* Pull the latest Netdata Docker image
* Start the container with required host mounts and capabilities

---

### 2. Verify the container is running

```sh
docker ps
```

You should see a container named `netdata` in the list.

---

### 3. Access the Netdata dashboard

Open your browser and visit:
[http://localhost:19999](http://localhost:19999)

---

## 🖼 Example Screenshots

| Dashboard Overview                                                                            | CPU Metrics                                                                             | Memory Usage                                                                               |
| --------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ |
| ![Dashboard](https://github.com/user-attachments/assets/9543f9f5-475b-4c12-b170-11f31a4b52e1) | ![CPU](https://github.com/user-attachments/assets/f4c206f9-7f2c-4cf8-96e6-a11ccb9c8688) | ![Memory](https://github.com/user-attachments/assets/b6eaa9ab-825b-4d7e-be50-4e0f1af64d22) |

| Disk I/O                                                                                 | Network Activity                                                                            |
| ---------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| ![Disk](https://github.com/user-attachments/assets/3460d595-9501-41eb-875c-f6d0a1148eb1) | ![Network](https://github.com/user-attachments/assets/e412a4ce-4d29-4573-910a-9c198c014559) |

---

## ⚠ Notes

* Ensure that no other service is using **port 19999**.
* If you stop the container, your metrics history will be lost unless you persist volumes.
* To stop Netdata:

  ```sh
  docker stop netdata
  docker rm netdata
  ```

---



