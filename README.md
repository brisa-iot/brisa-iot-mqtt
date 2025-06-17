# brisa-iot-mqtt

This project provides a ready-to-use MQTT broker (Eclipse Mosquitto) deployment, along with InfluxDB and Telegraf, using Docker Compose.

## How to Deploy the Broker

The MQTT broker and related services are managed using Docker Compose. This makes it easy to start, stop, and manage all components with a single command.

### Prerequisites

- [Docker](https://docs.docker.com/get-docker/) installed
- [Docker Compose](https://docs.docker.com/compose/install/) installed

### Steps to Deploy

1. **Clone this repository (if you haven't already):**
   ```sh
   git clone https://github.com/brisa-iot/brisa-iot-mqtt.git
   cd brisa-iot-mqtt
   ```

2. **(Optional) Adjust configuration files:**
   - Edit `./config/mosquitto.conf` for Mosquitto settings.
   - Edit `./telegraf/etc/telegraf.conf` for Telegraf.
   - Edit `configuration.env` for InfluxDB environment variables.

3. **Start all services:**
   ```sh
   docker compose up -d
   ```
   This will start:
   - **Mosquitto** (MQTT broker) on ports `1883` (MQTT) and `9001` (WebSockets)
   - **InfluxDB** on port `8086`
   - **Telegraf** on port `8125/udp`

4. **Verify the broker is running:**
   - Use an MQTT client to connect to `localhost:1883`.

### Stopping the Services

To stop and remove all containers:
```sh
docker compose down
```

## Data Persistence

- Mosquitto data and logs are stored in the `./data` and `./log` directories.
- InfluxDB data is persisted in the `influxdb_data` Docker volume.

## Notes

- All services are connected via the `telegraf_network` Docker network.
- You can customize each service by editing their respective configuration files before starting the stack.
- For production, consider securing Mosquitto with authentication and TLS.

```# brisa-iot-mqtt

This project provides a ready-to-use MQTT broker (Eclipse Mosquitto) deployment, along with InfluxDB and Telegraf, using Docker Compose.

## How to Deploy the Broker

The MQTT broker and related services are managed using Docker Compose. This makes it easy to start, stop, and manage all components with a single command.

### Prerequisites

- [Docker](https://docs.docker.com/get-docker/) installed

### Steps to Deploy

1. **Clone this repository (if you haven't already):**
   ```sh
   git clone https://github.com/brisa-iot/brisa-iot-mqtt.git
   cd brisa-iot-mqtt
   ```

2. **(Optional) Adjust configuration files:**
   - Edit `./config/mosquitto.conf` for Mosquitto settings.
   - Edit `./telegraf/etc/telegraf.conf` for Telegraf.
   - Edit `configuration.env` for InfluxDB environment variables.

3. **Start all services:**
   ```sh
   docker-compose up -d
   ```
   This will start:
   - **Mosquitto** (MQTT broker) on ports `1883` (MQTT) and `9001` (WebSockets)
   - **InfluxDB** on port `8086`
   - **Telegraf** on port `8125/udp`

4. **Verify the broker is running:**
   - Use an MQTT client to connect to `localhost:1883`.

### Stopping the Services

To stop and remove all containers:
```sh
docker-compose down
```

## Data Persistence

- Mosquitto data and logs are stored in the `./data` and `./log` directories.
- InfluxDB data is persisted in the `influxdb_data` Docker volume.

## Notes

- All services are connected via the `telegraf_network` Docker network.
- You can customize each service by editing their respective configuration files before starting the stack.
- For production, consider securing Mosquitto with authentication and TLS.
