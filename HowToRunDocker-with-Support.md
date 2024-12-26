
# **How to Run: Docker-files-for-ROC-toolkit-Linux-and-embedded**

## **Overview**

This repository provides Dockerfiles for CI builds and end-user images for cross-compilation using the Roc Toolkit. Docker images are built and pushed to Docker Hub under the `rocstreaming` organization. This guide will show you how to build and manage Docker images locally.

**I am providing support for running the open code and helping you with the setup and usage of the Docker images. If you encounter any issues or need further assistance, feel free to reach out!**

---

## **💡 Prerequisites**
Make sure you have the following before running the script:

- **Python 3.6+**: Ensure you have Python installed.
- **Docker**: Docker should be set up and running on your machine.
- **Permissions**: Ensure you have the necessary permissions to run Docker commands.

---

## **🛠 Usage**

### **1️⃣ Build a Single Image**

To build a specific image:

```bash
./make.py [OPTIONS...] IMAGE[:TAG]
```

#### **Example:**
```bash
./make.py env-ubuntu:20.04
```
This will build the `env-ubuntu` image with the `20.04` tag.

---

### **2️⃣ Build Multiple Images**

You can build multiple images or tags in a single command:

```bash
./make.py [OPTIONS...] IMAGE[:TAG] IMAGE[:TAG]
```

#### **Example:**
```bash
./make.py env-fedora env-ubuntu:20.04 env-ubuntu:22.04
```
This builds all tags for `env-fedora` and two specific tags for `env-ubuntu`.

---

### **3️⃣ Build All Images**

To build all available images in the repository:

```bash
./make.py
```

---

### **4️⃣ Dry Run Mode (Simulate)**

To **preview** the actions without actually executing them (dry run):

```bash
./make.py -n
```

This will print the commands to be executed without running them.

---

### **5️⃣ Push Images After Build**

To **automatically push** images to Docker Hub after building:

```bash
./make.py --push IMAGE[:TAG]
```

#### **Example:**
```bash
./make.py --push env-ubuntu:20.04
```

---

### **6️⃣ Advanced Options**

- **🚫 Disable Cache**: Skip Docker's build cache.
  
  ```bash
  ./make.py --no-cache IMAGE[:TAG]
  ```

- **⛔ Disable Pull**: Prevent pulling the latest base image during the build.
  
  ```bash
  ./make.py --no-pull IMAGE[:TAG]
  ```

- **📂 Use Build Cache**: Specify directories for caching during the build process.
  
  - **Load Cache**:
    ```bash
    ./make.py --cache-from /path/to/cache IMAGE[:TAG]
    ```

  - **Save Cache**:
    ```bash
    ./make.py --cache-to /path/to/cache IMAGE[:TAG]
    ```

---

## **🔍 Help Command**

To view all available options and their descriptions:

```bash
./make.py --help
```

---

## **📁 Repository Structure**

- **`images/`**: Contains subdirectories for each Docker image.
- **`images.csv`**: Defines build parameters for each image (e.g., Dockerfile paths, build arguments, tags, and target OS).

---

## **📊 Example Workflows**

### **Build an Image Without Pushing**:
```bash
./make.py env-ubuntu:20.04
```

### **Build All Images with Cache**:
```bash
./make.py --cache-from /path/to/cache --cache-to /path/to/cache
```

### **Simulate Actions Without Running Them**:
```bash
./make.py -n
```

---

## **❓ Contact**

For questions or issues, please open an issue on the repository's **GitHub Issue Tracker**.

---

