# Homecarespa - On-Demand Massage Service Platform

Homecarespa is an on-demand mobile platform that facilitates massage services between users and professional masseuses. The application provides users with the convenience of finding and booking nearby professional massage services based on their location. Additionally, it offers multiple payment options, including e-wallets (OVO, GoPay, DANA), and cryptocurrencies (USDT, Digital Rupiah).

## Components Included

The Homecarespa platform includes the following components:

- **RabbitMQ**: Used as a message broker to facilitate communication between various services in the platform.
- **Vault**: Used for secrets management, providing a secure way to store and access sensitive information.
- **Websocket Server**: Enables real-time communication between clients and the server, allowing for instant updates and notifications.
- **Database with PostGIS**: The spatial database with PostGIS extension allows the platform to handle geospatial data efficiently.
- **Redis**: Used as a caching layer to improve application performance and reduce database load.
- **Mail Service**: Provides email functionalities for sending notifications and updates to users and administrators.
- **Notification Service**: Handles in-app and push notifications to keep users informed about their bookings and other activities.
- **Backend API**: The core of the platform, responsible for handling user requests, managing bookings, and interacting with various services.
- **Envoy and Traefik**: Used as the reverse proxy and load balancer to route and manage incoming requests to the appropriate services, providing scalability and reliability.

Please note that all these components are automatically installed and configured during the Terraform setup or manual installation process.

## Configuration

Platform settings can be configured in the `config/app.yml` file. This file contains various parameters that control the behavior of the Homecarespa platform. Please make sure to update the necessary configurations, such as API keys, database connection settings, and other options before deploying the platform.

## Applying Configuration to Server

Once you have made the necessary changes to the configuration in `config/app.yml`, you can apply it to the server using the following rake task:

```
rake render:config
```

This task will render the configuration and apply it to the server, making sure that the platform uses the updated settings.

## Installation

### Terraform Installation

1. **Clone Repository**
   Clone the Homecarespa repository to your local machine:
   ```
   git clone https://github.com/nusatech-cv/homecarespa.git
   cd homecarespa
   ```

2. **Update IP Address and Username**
   Open `config/app.yml` in a text editor and update the `ip_address` and `user` fields under the `server` section with the appropriate server details.

3. **Apply Terraform Changes**
   Initialize Terraform and apply the changes to set up the infrastructure:
   ```
   rake terraform:install
   rake terraform:apply
   ```

### Manual Installation

1. **SSH to Server**
   Connect to your server using SSH. Replace `ip_server` with the actual IP address of your server:
   ```
   ssh user@ip_server
   ```

2. **Install Ruby version 3.0.5**
   Install Ruby version 3.0.5 on your server. You can refer to the documentation or package manager of your server's operating system for installation instructions.

3. **Clone Repository**
   Clone the Homecarespa repository to your server:
   ```
   git clone https://github.com/nusatech-cv/homecarespa.git
   cd homecarespa
   ```

4. **Install Dependencies**
   Install the required Ruby dependencies using Bundler:
   ```
   bundle install
   ```

5. **Render Configuration and Start Platform**
   Use the following rake task to render the configuration and start the platform:
   ```
   rake service:all
   ```

6. **Stop All Containers**
   To stop all running Docker containers on the server, use the following command:
   ```
   rake docker:down
   ```

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more information.

## Contact

For any inquiries or support, please contact us at support@nusatech.id.
