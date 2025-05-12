# Game Statistic Application

The Game Statistic Application is a full-stack project for managing and visualizing video game data. It consists of two parts: **Backend** (REST API) and **Frontend** (web interface).

## Architecture

- **Backend**: A Flask-based application for managing video game data, including CRUD operations and statistics.
- **Frontend**: A React-based application using Material-UI to display data in tables and charts.

## Key Technologies

- **Backend**:
  - Flask, SQLAlchemy, Marshmallow
  - PostgreSQL
  - Docker
- **Frontend**:
  - React, Material-UI
  - Nginx
  - Docker

## Installation and Setup

### 1. Clone the Repository

```bash
git clone --recurse-submodules https://github.com/xottab-ops/game-stats-app.git
```

### 2. Configure Environment Variables

#### Backend

Ensure the `.env` file in the project root is configured as follows:

```dotenv
# Flask
FLASK_APP=app.py
FLASK_ENV=development
FLASK_INNER_PORT=5000
FLASK_OUTER_PORT=5000

# Database
POSTGRES_DB=flask_db
POSTGRES_USER=flask_user
POSTGRES_PASSWORD=flask_password
POSTGRES_HOST=db
POSTGRES_PORT=5432
DATABASE_URI=postgresql+psycopg2://${POSTGRES_USER}:${POSTGRES_PASSWORD}@${POSTGRES_HOST}:${POSTGRES_PORT}/${POSTGRES_DB}

# TypeScript
REACT_APP_PORT=3000
REACT_APP_API_PORT=5000
REACT_APP_API_HOST=http://flask_app
```

### 3. Run with Docker

Ensure Docker is installed and running. From the root folder of the project, execute:

```bash
docker-compose up --build
```

This will create and start containers for the backend, frontend, and database.

### 4. Import Data

To load data from the `steam.csv` file, run:

```bash
docker exec -it flask_app python import_data.py
```

### 5. Access the Application

- **Backend API**: [http://localhost:5000](http://localhost:5000)
- **Frontend**: [http://localhost:3000](http://localhost:3000)

## Project Structure

```
game-stats-app/
├── game-stats-backend/   # Backend application
│   ├── app/              # Flask application source code
│   │   ├── dto/          # Data Transfer Objects (DTOs) for structured data handling
│   │   ├── models/       # Database models
│   │   ├── routes/       # API routes
│   │   ├── schemas/      # Data serialization schemas
│   │   ├── seeds/        # Scripts for seeding the database
│   │   ├── services/     # Business logic and data handling
│   │   ├── config.py     # Application configuration
│   │   ├── extensions.py # Flask extensions initialization
│   │   ├── __init__.py   # Application initialization
│   ├── static/           # Static files (e.g., steam.csv)
│   ├── import_data.py    # Script to import data into the database
│   ├── requirements.txt  # Python dependencies
│   ├── docker-compose.yml# Docker Compose configuration
│   ├── .env              # Environment variables
│   └── README.md         # Project documentation
├── game-stats-frontend/  # Frontend application
│   ├── src/              # React application source code
│   │   ├── components/   # Reusable UI components
│   │   ├── hooks/        # Custom React hooks for data fetching and logic
│   │   ├── images/       # Static image assets
│   │   ├── pages/        # Includes different pages like charts and lists
│   │   ├── services/     # API client for backend communication
│   │   ├── styles/       # Global and component-specific styles
│   │   ├── types/        # TypeScript interfaces and types
│   │   ├── utils/        # Utility functions for data formatting
│   ├── Dockerfile        # Configuration for building the Docker image
│   ├── docker-compose.yaml # Configuration for running the application with Docker
│   ├── .env              # Environment variables
│   └── README.md         # Project documentation
├── docker-compose.yml    # Global Docker configuration
└── README.md             # Unified documentation
```

## License

This project is licensed under the MIT License. See the `LICENSE` file for details.

## Contributing
Contributions are welcome! Please fork the repository and submit a pull request for any changes or improvements.

## Acknowledgments
- Thanks to the open-source community for the libraries and tools used in this project.
- Special thanks to the contributors for their valuable input and feedback.
- Inspired by various resources and tutorials on Flask, React, and Docker.

