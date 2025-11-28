espite the resource constraint, significant progress was made, showcasing system administration and troubleshooting expertise.

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
