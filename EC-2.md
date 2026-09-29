# AWS EC2

Amazon EC2 (Elastic Compute Cloud) is a web service that provides resizable compute capacity in the AWS Cloud.

---

# Types of EC2 Instances

## 🔹 1. General Purpose Instances

### Description

Balanced compute, memory, and networking resources.

### Use Cases

- Web servers
- Small to medium databases
- Development and testing environments

### Examples

- t2
- t3
- t4g
- m5
- m6g

---

## 🔹 2. Compute Optimized Instances

### Description

High-performance processors for compute-intensive tasks.

### Use Cases

- High-performance web servers
- Gaming servers
- Batch processing

### Examples

- c5
- c6g

---

## 🔹 3. Memory Optimized Instances

### Description

Optimized for memory-intensive applications.

### Use Cases

- In-memory databases
- Real-time big data analytics

### Examples

- r5
- r6g
- x1
- x2idn

---

## 🔹 4. Storage Optimized Instances

### Description

Designed for workloads that require high disk throughput and low-latency storage.

### Use Cases

- Data warehousing
- Log processing
- Big data workloads

### Examples

- i3
- i4i
- d2
- d3

---

## 🔹 5. Accelerated Computing Instances

### Description

Use hardware accelerators such as GPUs or FPGAs to perform specialized workloads.

### Use Cases

- Machine learning
- Artificial intelligence
- Video rendering

### Examples

- p3
- p4
- g4
- g5
- f1

---

## 🔹 6. High Performance Computing (HPC) Instances

### Description

Designed for high-performance and scientific computing workloads.

### Use Cases

- Scientific simulations
- Weather forecasting
- Financial modeling

### Examples

- hpc6a

---

## ✅ Summary Table

| Instance Type | Main Feature | Use Case Example |
|---|---|---|
| General Purpose | Balanced resources | Web applications |
| Compute Optimized | High CPU performance | Gaming, processing |
| Memory Optimized | High RAM | Databases |
| Storage Optimized | Fast storage | Big data |
| Accelerated Computing | GPU/FPGA | AI/ML |
| HPC | High-performance computing | Scientific workloads |

---

# Key Pair (Login)

A key pair is used to securely connect to an EC2 instance.

A key pair consists of:

- **Public Key** → Stored by AWS
- **Private Key** → Stored by the user

When launching an EC2 instance, ensure that you have access to the selected key pair.

For Linux instances, the private key is commonly downloaded as a `.pem` file and used for SSH access.

---

# Bash Script Example

The following Bash script updates the system, installs Nginx, starts the Nginx service, and creates a custom HTML page.

```bash
#!/bin/bash

# Update system packages
echo "Updating system..."
sudo apt update -y

# Install Nginx
echo "Installing Nginx..."
sudo apt install nginx -y

# Start and enable Nginx
echo "Starting Nginx service..."
sudo systemctl start nginx
sudo systemctl enable nginx

# Create HTML content
echo "Creating HTML file..."

sudo bash -c 'cat > /var/www/html/index.html <<EOF
<!DOCTYPE html>
<html>
<head>
    <title>My Web Server</title>
</head>
<body>
    <h1>Welcome to My Nginx Server!</h1>
    <p>This page is deployed using a Bash script.</p>
</body>
</html>
EOF'

# Restart Nginx to apply changes
echo "Restarting Nginx..."
sudo systemctl restart nginx

echo "Setup complete! Open your browser and visit your server IP."
