# Full-Stack Forum Application

## 📖 Overview
A lightweight, fully functional web forum built from scratch using Go, SQLite3, and Vanilla JavaScript. This application provides a platform for users to register, create and categorize posts, comment on discussions, and engage through a dynamic like/dislike interaction system.

## 🚀 Features
* **User Authentication & Authorization**: Secure registration, login, and logout functionality. Passwords are encrypted using `bcrypt`, and sessions are securely managed via UUID tokens stored in cookies.
* **Post Management**: Users can create posts and assign them to predefined categories (Technology, Lifestyle, Travel, Food, Sport, Other). Includes a 1-second cooldown rate limiter on post creation to prevent spam.
* **Commenting System**: Dynamic, real-time commenting on posts allowing for continuous discussion threads.
* **Engagement (Likes/Dislikes)**: Users can upvote or downvote both posts and individual comments. The UI updates counts and active states asynchronously.
* **Advanced Filtering**: Filter the main feed by specific categories, or filter by ownership to view "My Posts" or "Liked Posts".
* **Security Measures**: Protection against Cross-Site Scripting (XSS) via strict HTML string escaping for all user inputs.
* **Containerized Environment**: Includes a Dockerfile and setup script for seamless, isolated deployment.

## 🛠️ Tech Stack
* **Backend**: Go (Golang) 1.21
* **Frontend**: HTML5, CSS3, Vanilla JavaScript (No external UI frameworks)
* **Database**: SQLite3 (`github.com/mattn/go-sqlite3`)
* **Security & Utils**: `golang.org/x/crypto/bcrypt`, `github.com/gofrs/uuid/v5`
* **Deployment**: Docker

## 📁 Project Structure
```text
├── auth/                   # Authentication and session management handlers
├── database/               # SQLite DB initialization and table schema definitions
├── handlers/               # HTTP request handlers (Posts, Comments, Categories, Interactions)
├── models/                 # Go data structures (Types)
├── pages/                  # HTML templates (e.g., index.html)
├── static/                 # Client-side assets (CSS, Vanilla JS, Images)
├── utils/                  # Helper utilities (e.g., HTML string escaping)
├── Dockerfile              # Docker image configuration (Alpine-based)
├── doit.sh                 # Shell script to automate Docker build and run
├── main.go                 # Application entry point and router configuration
└── go.mod / go.sum         # Go module dependencies
```

## ⚙️ Prerequisites
* [Docker](https://www.docker.com/) (Recommended for rapid deployment)
* **OR** [Go 1.21+](https://go.dev/dl/) and a GCC compiler (required for CGO and SQLite3) if running locally.

## 🚀 Getting Started

### Option 1: Run with Docker (Recommended)
A bash script (`doit.sh`) is provided to automate the Docker image build and container deployment.

1. Make the script executable:
   ```bash
   chmod +x doit.sh
   ```
2. Run the deployment script:
  ```bash
  ./doit.sh
  ```
3. Open your web browser and navigate to: http://localhost:4848/

### Option 2: Run Locally
1. Clone the repository and navigate into the project directory:
```bash
cd forum
```

2. Download the required Go modules:
```bash
go mod download
```

3. Ensure CGO is enabled (required by the SQLite driver), then start the server:
```bash
export CGO_ENABLED=1
go run main.go
```

4. Open your web browser and navigate to: http://localhost:4848/

## 🛡️ Security & Architecture Notes
* **Database:** A single `forum.db` file is generated in the root directory upon initialization. It uses foreign key constraints and `ON DELETE CASCADE` to maintain data integrity.
* **Routing:** Utilizes Go's standard `net/http` package for routing RESTful endpoints and serving static files.
* **State Management:** The frontend relies on Vanilla JS to fetch session state (`/check-session`) and dynamically render authorized UI components without page reloads.

## 👨‍💻 Author
**Mouad El-Janati** Zone01 Oujda
