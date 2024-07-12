# Full-Stack FastAPI and React Template

Welcome to the Full-Stack FastAPI and React template repository. This repository serves as a demo application for showcasing how to set up and run a full-stack application with a FastAPI backend and a ReactJS frontend using ChakraUI.

## Project Structure

The repository is organized into two main directories:

- **frontend**: Contains the ReactJS application.
- **backend**: Contains the FastAPI application and PostgreSQL database integration.

## Getting Started

1. **Clone the Repository:**
   git clone <forked-repository-url>
   cd <repository-directory>

2. **Build and Run the Services:**
   docker-compose up -d --build

3. **Access the Application:**

- Frontend: http://localhost/
- Backend API: http://localhost/api/
- Adminer (Database UI): http://localhost:8080/

### Deployment on Amazon Web Service

To deploy the application on Amazon Web Service and set up HTTPS with Let's Encrypt, follow these steps:

1. **Prepare Docker Compose File:**
   Modify `docker-compose.yml` as necessary for production environment settings (e.g., environment variables, volume mounts).

2. **Set Up a Amazon Web Service EC2 Instance:**

- Create an EC2 (virtual machine) on AWS with Docker installed.
- Download your Private Key from AWS
- SSH into your sserver using the private key.

3. **Deploy Application to EC2-Instance:**

- SSH into your ec2 instance using:
  ```
  ssh ubuntu@your-ec2-instance-ip
  ssh -i "xxxx.pem" ubuntu@your-ec2-instance-ip
  ```
- Clone your repository inside the server:
  ```
  git clone <repository-url>
  cd <repository-directory>
  ```
- Build and run the Docker containers:
  ```
  docker-compose up -d --build
  ```

4. **Set Up Domain and HTTPS:**

- Obtain a domain name from a registrar like Namecheap or GoDaddy.
- Configure DNS records to point to your Droplet's IP address.
- Install Certbot on your Droplet:
  ```
  sudo apt update
  sudo apt install certbot
  ```
- Generate SSL certificate using Certbot:
  ```
  sudo certbot certonly --nginx -d your-domain.com -d www.your-domain.com
  ```
- Update Nginx configuration (`nginx.conf`) to use SSL certificates and handle HTTPS traffic.

## Nginx Configuration

Modify Nginx configuration (`nginx.conf`) to handle routing for frontend and backend services, ensuring:

- Frontend serves on root (http://domain/)
- Backend APIs proxy to `/api` (http://domain/api/)
- Adminer accessible via subdomain (http://db.domain/)