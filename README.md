# Keycloak Container Setup

Welcome to the Keycloak container setup guide. This README will guide you through setting up a Keycloak container that connects to a PostgreSQL database, utilizing Docker.

## Prerequisites

Ensure Docker is installed on your machine. If Docker is not installed, please download it from [Docker's official site](https://www.docker.com/get-started).

## Local Setup

Follow these steps to configure your Keycloak container:

1. **Set Environment Variables**

   Create a `.env` file in your project root, if it does not already exist, and add the following environment variables:

   ```
   KEYCLOAK_VERSION=<desired Keycloak version>
   PORT_KEYCLOAK=<desired port for Keycloak>
   POSTGRESQL_USER=<username for PostgreSQL database>
   POSTGRESQL_PASS=<password for PostgreSQL user>
   POSTGRESQL_DB=<database name for Keycloak data>
   KEYCLOAK_ADMIN=<admin username>
   KEYCLOAK_ADMIN_PASSWORD=<admin password>
   ```

   Replace the placeholders with the actual values you want to use:
   - `KEYCLOAK_VERSION`: Specify the version of Keycloak you wish to deploy, e.g., "22.0.4".
   - `PORT_KEYCLOAK`: Set the port on which Keycloak will be accessible, e.g., "8080".
   - `POSTGRESQL_USER`, `POSTGRESQL_PASS`, and `POSTGRESQL_DB`: Provide the credentials and database name for Keycloak's backend PostgreSQL database.
   - `KEYCLOAK_ADMIN` and `KEYCLOAK_ADMIN_PASSWORD`: Define the admin username and password for the Keycloak admin console.

2. **Launch the Container**

   Use the Docker Compose command below to start your Keycloak container. Ensure your `docker-compose.yml` file is configured to use the variables set in your `.env` file. The command to start the container in detached mode is:

   ```bash
   docker compose up -d
   ```

## Usage

Once the container is running, access the Keycloak admin console through your web browser by navigating to `http://localhost:<PORT_KEYCLOAK>`, replacing `<PORT_KEYCLOAK>` with the port number you set in the `.env` file.

Login with the `KEYCLOAK_ADMIN` and `KEYCLOAK_ADMIN_PASSWORD` credentials to configure realms, clients, and users as per your requirements.

## Configuration Export and Import

To facilitate configuration management, a batch file is provided to export the entire Keycloak setup. Run the `exportKeycloak.bat` located under `./utility/` to export your current Keycloak configuration. This process will save the configuration as a JSON file in `./import/keycloak-no-fomo-taskmanager.json`.

When you restart the container, this JSON file is automatically imported, ensuring that your Keycloak configuration is preserved and reinstated. 

## Support

For any issues or further configuration needs, refer to the [Keycloak official documentation](https://www.keycloak.org/documentation.html) or the project's issues page on GitHub.
