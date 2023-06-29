# Apache Guacamole Docker Installation

This repository provides a Docker Compose configuration file for installing Apache Guacamole on a Linux server. Apache Guacamole is a clientless remote desktop gateway that allows you to access remote Desktop and Server machines via a web browser. It supports protocols like VNC, RDP, and SSH and utilizes HTML5 for remote connections.

## Requirements

To follow this tutorial, you need a Linux server or laptop.

## Installation Steps

1. Install Docker and Docker Compose:
   - Download and execute the convenience script provided by Docker.

2. Clone the repository:
   ```
   git clone https://github.com/kkpkishan/apache-guacamole-docker.git
   ```

3. Navigate to the cloned repository:
   ```
   cd apache-guacamole-docker
   ```

4. Create the `.env` file:
   - Create a file named `.env` inside the `/guacamole` directory to store the database credentials.

5. Enable session recordings in-browser:
   - After running the `docker-compose up -d` command, execute the following command:
     ```
     chmod -R 777 ./recordings
     ```
   - This will enable session recordings and set the recording path to `/opt/guacamole/recording`. The recording name will be based on the history UUID (${HISTORY_UUID}).

6. Access Apache Guacamole:
   - Once the containers are up and running, you can access Apache Guacamole by navigating to the server's IP address or hostname using a web browser. Use the following URL:
   
     http://\<Your IP\>

7. Default Admin Credentials:
   - The default admin credentials for Apache Guacamole are:
     - Username: guacadmin
     - Password: guacadmin

8. Additional Extensions (if used):
   - If you have used any additional extensions, the available extensions can be found in the `guacamole/etc/available-extensions` directory. Here is a list of some available extensions:
     - guacamole-1.5.0.war
     - guacamole-auth-quickconnect-1.5.0.jar
     - guacamole-auth-duo-1.5.0.jar
     - guacamole-auth-sso-cas-1.5.0.jar
     - guacamole-auth-header-1.5.0.jar
     - guacamole-auth-sso-openid-1.5.0.jar
     - guacamole-auth-jdbc-mysql-1.5.0.jar
     - guacamole-auth-sso-saml-1.5.0.jar
     - guacamole-auth-jdbc-postgresql-1.5.0.jar
     - guacamole-auth-totp-1.5.0.jar
     - guacamole-auth-jdbc-sqlserver-1.5.0.jar
     - guacamole-history-recording-storage-1.5.0.jar
     - guacamole-auth-json-1.5.0.jar
     - guacamole-vault-ksm-1.5.0.jar
     - guacamole-auth-ldap-1.5.0.jar

## Docker Compose Configuration

The `docker-compose.yml` file in this repository contains the declaration of all the Docker containers required to run Apache Guacamole. Guacamole is composed of three containers:

1. `guacamole_frontend`: The web UI, which users interact with.
2. `guacamole_backend`: `guacd` is the core of Guacamole. It dynamically loads support for remote desktop protocols (client plugins) and connects them to remote desktops

 based on instructions received from the web application.
3. `guacamole_database`: The database used by Guacamole for authentication and storage of connection configuration data.

## Additional Information

For more information about Apache Guacamole and its features, please refer to the [official Apache Guacamole documentation](https://guacamole.apache.org/).

Recordings of connections can be found using the recording storage extension, as long as those connections are configured in either of two ways, involving naming a file or directory with the history UUID (${HISTORY_UUID}).

**Note:** Please refer to the original [repository](https://github.com/kkpkishan/apache-guacamole-docker) for any updates or changes to the Docker Compose configuration file.

**Disclaimer:** This README.md file is a simplified version of the original documentation provided by the repository mentioned above. It serves as a guide and may not cover all possible scenarios or configurations. For a complete understanding of Apache Guacamole installation and usage, refer to the official documentation.
