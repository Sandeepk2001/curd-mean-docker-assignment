## 📄 Troubleshooting and Limitation Report: MEAN Stack Deployment

**Project Status:** Deployment Unfinished (Blocked by Infrastructure Limitation)

This report documents the severe resource constraints encountered during the Docker deployment, which prevented successful completion of the final build and application launch. It also details the advanced troubleshooting steps executed to recover the environment.

---

### 1. ⚙️ Environment and Resource Constraints (Root Cause)

The primary reason for the task's failure was an **insufficiently sized AWS EBS Root Volume**. The volume size could not accommodate the temporary cache and dependency downloads required by the Docker and Node.js build process.

| Resource | Specification | Final Status / Error |
| :--- | :--- | :--- |
| **AWS Instance Type** | t3.micro | Adequate for runtime, but limited for build. |
| **Root Volume (EBS)** | **8 GB** (Default Size) | **CRITICAL FAILURE POINT.** Insufficient capacity. |
| **Disk Usage (Initial)** | 95% Used | Initial instability due to high default usage. |
| **Disk Usage (Final)** | **97% Used** (approx. 232MB Available) | **Failure State:** Disk space exhausted during NPM dependency downloads. |

**Final Error Message (Build Failure Point):**
> `write /app/node_modules/...: No space left on device`
> `ERROR: Service 'frontend' failed to build: Build failed`

---

### 2. ✅ Completed Tasks and Demonstrated Skills

Despite the resource constraint, significant progress was made, showcasing system administration and troubleshooting expertise.

| Category | Task Completed | Skill Demonstrated |
| :--- | :--- | :--- |
| **System Stabilization** | Cleared 1.53 GB of disk space using `docker system prune -a` and other system cleanups, reducing initial usage from 95% to 71%. | **DevOps, Disk Cleanup, Resource Management.** |
| **Filesystem Recovery** | Fixed a directory name corruption issue (`crud-mean-docker-assignment`) by using **Inode Access** (`ls -iaF` and `find . -inum [ID]...`) to rename the folder to `myproject`. | **Advanced Linux Filesystem Troubleshooting.** |
| **Project Setup** | Successfully navigated to the project directory (`~/myproject`), confirmed file integrity, and initiated the Docker build process. | Git familiarity and environment readiness. |

---

### 3. ❌ Uncompleted Tasks and Proposed Solution

| Task | Status | Reason for Failure |
| :--- | :--- | :--- |
| **Full `docker-compose up --build`** | Failed | Disk exhaustion during the Node.js/NPM installation step. |
| **Application Deployment** | Unfinished | Depends on successful container builds. |

**Required Action to Complete Task:**

The environment requires an infrastructure modification to proceed:

* **The EBS Root Volume size must be increased** from **8 GB** to a minimum of **20 GB** to provide the necessary space for Docker image layers and NPM dependency compilation.