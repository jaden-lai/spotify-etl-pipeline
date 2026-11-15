# Spotify Data Engineering Pipeline

This project focuses on building a data engineering pipeline for streaming user data from the Spotify API, storing the data in PostgreSQL, and processing it for analysis. The pipeline facilitates easy access to users' Spotify activity, including the most recently played tracks. The project also lays the groundwork for future automation using Apache Airflow.

## Table of Contents

- [Project Overview](#project-overview)
- [Technologies Used](#technologies-used)
- [Installation](#installation)
- [Usage](#usage)
- [Future Work](#future-work)
- [Contributors](#contributors)

## Project Overview

The **Spotify Data Engineering Pipeline** ingests user data from the Spotify API and stores it in a PostgreSQL database for later analysis. The pipeline supports the retrieval of the **top 100 most recently played tracks** of a Spotify user. The project also involves setting up the framework for task automation using Apache Airflow, although this component is partially implemented.

The core functionality includes:

1. **Data Extraction**: Fetching the user’s Spotify activity data (recently played tracks).
2. **Data Transformation**: Storing the data into a PostgreSQL database.
3. **Data Loading**: Creating tables and inserting data into the PostgreSQL database.
4. **Scheduling**: Implementing a partial Apache Airflow framework to automate data extraction tasks.

## Technologies Used

- **Python**: Main language used for building the pipeline.
- **PostgreSQL**: Relational database to store and process the data.
- **SQLAlchemy**: Python SQL toolkit and ORM for database interactions.
- **Spotify API**: Provides access to Spotify's user data.
- **Apache Airflow (Partial)**: For orchestrating and scheduling tasks (in progress).
- **GitHub**: Version control for the project.
- **Docker** (Planned): Containerizing the pipeline for reproducibility.

## Installation

### Prerequisites

Make sure you have the following tools installed:
- Python 3.7+
- PostgreSQL and pgAdmin4
- Git

### Steps

1. Clone the repository and move into it:

    ```bash
    git clone https://github.com/jaden-lai/spotify-etl-pipeline.git
    cd spotify-etl-pipeline
    ```

2. Install the required Python packages:

    ```bash
    pip install -r requirements.txt
    ```

3. Set up PostgreSQL: install it if needed and create a database for the Spotify data.

4. Create a Spotify app in the [Spotify Developer Dashboard](https://developer.spotify.com/dashboard) to get a client ID and client secret, and add a redirect URI to the app's settings.

5. Create a `.env` file in the project root (it's git-ignored, so your credentials stay local):

    ```bash
    SPOTIPY_CLIENT_ID=your_client_id
    SPOTIPY_CLIENT_SECRET=your_client_secret
    SPOTIPY_REDIRECT_URI=http://127.0.0.1:8888/callback
    DATABASE_URL=postgresql://user:password@localhost:5432/your_database
    ```

    `SPOTIPY_REDIRECT_URI` must match the redirect URI set in your Spotify app.

## Usage

From the project root, run the pipeline:

```bash
python -m scripts.main
```

The first run opens a browser window to log in to Spotify. The resulting token is cached in `.cache`, which is also git-ignored.
