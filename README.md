In this DevOps task, you need to build and deploy a full-stack CRUD application using the MEAN stack (MongoDB, Express, Angular 15, and Node.js). The backend will be developed with Node.js and Express to provide REST APIs, connecting to a MongoDB database. The frontend will be an Angular application utilizing HTTPClient for communication.  

The application will manage a collection of tutorials, where each tutorial includes an ID, title, description, and published status. Users will be able to create, retrieve, update, and delete tutorials. Additionally, a search box will allow users to find tutorials by title.

## Project setup

### Node.js Server

cd backend

npm install

You can update the MongoDB credentials by modifying the `db.config.js` file located in `app/config/`.

Run `node server.js`

### Angular Client

cd frontend

npm install

Run `ng serve --port 8081`

You can modify the `src/app/services/tutorial.service.ts` file to adjust how the frontend interacts with the backend.

Navigate to `http://localhost:8081/`

===========================================================================================================================

#  MEAN Stack CRUD Application
Dockerized | Deployed on AWS EC2 | CI/CD Enabled

---

#  Project Overview

This is a full-stack MEAN (MongoDB, Express, Angular, Node.js) CRUD application.

The project demonstrates:

- Full-stack development
- Docker containerization
- Docker Compose orchestration
- AWS EC2 deployment
- GitHub Actions CI/CD automation

---

#  Project Structure
mean-dd-task/
│
├── backend/
│ └── Dockerfile
│
├── frontend/
│ └── Dockerfile
│
├── docker-compose.yml
└── .github/workflows/deploy.yml

Step 1: Install Backend Dependencies
cd backend
npm install

Start backend:

npm start

Backend runs at:

http://localhost:8080
Step 2: Install Frontend Dependencies
cd frontend
npm install

Start frontend:

ng serve

Frontend runs at:

http://localhost:4200
🐳 2️⃣ Docker Setup (Local)
Step 3: Build Docker Images
Build Backend
cd backend

docker build -t User_Name/dd-backend:latest .
Build Frontend

cd frontend
docker build -t User_NAme/dd-frontend:latest .
Step 4: Run Using Docker Compose

Go to root directory:

docker-compose up -d

Check running containers:

docker ps

Access application:

http://localhost
☁️ 3️⃣ AWS EC2 Deployment (Production Setup)
Step 5: Launch EC2 Instance

OS: Ubuntu
Instance Type: t2.micro (or similar)
Open Security Group Ports:
22 (SSH)
80 (HTTP)
4200(Custom TCP)
5000(Custom TCP)

Step 6: Connect to EC2
ssh -i your-key.pem ubuntu@<EC2-Public-IP>
Step 7: Install Docker & Docker Compose
sudo apt update
sudo apt install docker.io docker-compose -y
sudo usermod -aG docker ubuntu

Logout and reconnect to apply docker permissions.

Step 8: Pull Docker Images from Docker Hub
docker pull User_Name/dd-backend:latest
docker pull User_NAme/dd-frontend:latest

Step 9: Create docker-compose.yml on EC2
services:
  mongodb:
    image: mongo:latest
    restart: always
    volumes:
      - mongo-data:/data/db

  backend:
    image: banda01/dd-backend:latest
    restart: always
    depends_on:
      - mongodb

  frontend:
    image: banda01/dd-frontend:latest
    restart: always
    ports:
      - "80:80"
    depends_on:
      - backend

volumes:
  mongo-data:
Step 10: Start Application
docker-compose up -d

Check running containers:

docker ps
Step 11: Access Application

Open browser:

http://<EC2-Public-IP>

Application should be live.

🔄 4️⃣ CI/CD Setup (GitHub Actions)
Step 1: Add GitHub Secrets

Go to:
Repository → Settings → Secrets and Variables → Actions
Add:
DOCKER_USERNAME
DOCKER_PASSWORD
EC2_HOST
EC2_USER
EC2_SSH_KEY

Step 11: Workflow File Location
.github/workflows/deploy.yml

Step 12: CI/CD Flow
On every push to main branch:
GitHub checks out code
Logs into Docker Hub
Builds Docker image
Pushes image to Docker Hub
SSH into EC2
Pulls latest image
Restarts containers

Deployment becomes automatic.

🌍 Live URL
http://<EC2-Public-IP>
✅ Verification Commands

Check containers:
docker ps
Check logs:
docker logs <container_name>
Stop containers:
docker-compose down
Restart containers:

docker-compose up -d
🎯 Conclusion

This project demonstrates:

End-to-end containerized full-stack deployment

Production-ready Angular build

Cloud deployment using AWS EC2

Automated CI/CD pipeline using GitHub Actions

Secure secret management

This version is:

✔ Clean  
✔ Step-by-step  
✔ Professional  
✔ Submission-ready  
✔ Easy for interviewer to reproduce  




