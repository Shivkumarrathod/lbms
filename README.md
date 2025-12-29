# Library Management System (LBMS)

A modern full-stack Library Management System built with a Monorepo structure, containerized with Docker, and automated with GitHub Actions.

## 🚀 Tech Stack

*   **Frontend**: Next.js 14, TypeScript, TailwindCSS
*   **Backend**: Node.js, Express.js, MongoDB Atlas
*   **DevOps**: Docker, Docker Compose, GitHub Actions (CI/CD)

## 📂 Project Structure

```
/
├── client/                 # Next.js Frontend
├── server/                 # Express.js Backend
├── .github/workflows/      # CI/CD Pipelines
├── docker-compose.yml      # Docker Orchestration
└── dev.sh                  # Local Development Helper Script
```

## 🛠️ Getting Started

### Prerequisites
*   Git
*   Docker & Docker Compose (optional for local dev, required for containerization)
*   Node.js (v20+)

### 1. Clone the Repository
```bash
git clone https://github.com/Shivkumarrathod/lbms.git
cd lbms
```

### 2. Environment Setup
Create a `.env` file in the `server` directory:
```bash
cp server/.env.example server/.env
# Edit server/.env and add your MONGO_URI
```

### 3. Running Locally
We have provided a helper script to manage local dependencies and run both services simultaneously.

```bash
chmod +x dev.sh
./dev.sh
```
*   **Frontend**: [http://localhost:3000](http://localhost:3000)
*   **Backend**: [http://localhost:5000](http://localhost:5000)

### 4. Running with Docker
Build and run the entire stack using Docker Compose:

```bash
docker-compose up --build
```
*Note: Ensure you have a valid .env file in place.*

## 🔄 DevOps Procedure

### Branching Strategy
We follow a strict Git Flow:
*   **`main`**: Production-ready code. Protected branch.
*   **`dev`**: Active development branch. All features merge here first.

### Workflow
1.  **Checkout `dev`**: Always start your work from the development branch.
    ```bash
    git checkout dev
    git pull origin dev
    ```
2.  **Develop**: Make changes and commit.
3.  **Push**: Push to `dev` to trigger the CI Pipeline.
    ```bash
    git push origin dev
    ```
4.  **CI Checks**: GitHub Actions will automatically:
    *   Install dependencies.
    *   Lint the code (ESLint).
    *   Verify Docker builds for both Client and Server.
5.  **Pull Request**: If CI passes (Green Check), raise a PR from `dev` to `main`.

## 🐳 Docker Images
*   **Server**: `lbms-server` (Alpine Node.js)
*   **Client**: `lbms-client` (Next.js Standalone Build)
