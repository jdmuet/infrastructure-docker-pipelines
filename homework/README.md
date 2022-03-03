# CVE-2022-0185 in Linux Kernel Can Allow Container Escape in Kubernetes/Docker


Article Link: 0https://blog.aquasec.com/cve-2022-0185-linux-kernel-container-escape-in-kubernetes

A new venerability was discovered recently that can allow users without privileges to escalate their 
rights to root. This will primarily be an issue if you have the Linux capablity of CAP_SYS_ADMIN. This  
reduces the risk but will mainly be an issue with Kubernetes cluster.
The CAP_SYS_ADMIN would need to be added in Docker for this to be an issue, either specifically
 or by using the --priviledged option when the container is started. However, users can still
exploit this by using the unshare Linux command. The seccomp filter in Docker automatically blocks the
unshare command but Kubernetes automatically disables that filters, so the issue can still apply.

How to prevent the vulnerability:
Apply the Linux patch as soon as possible.
Minimize the use of priviledged containers
Ensure that a seccomp filter is in place that blocks the unshare call (default for Docker)

 + Was the security practice or vulnerability you researched particular to Docker, or not?
    This is related to Docker and Kubernetes
  + Was the security practice or vulnerability related to the core docker system itself, the extended environment (e.g. Docker Hub), or Docker images (a.k.a. the software inside the Docker image)? 
    This effects Docker images.
  + Is this something that you should be concerned about within your particular company?
    No, this is disabled by default.
