# hello-node-clustering

A simple Node.js application to demonstrate the performance benefits of clustering and process management in handling concurrent requests.

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Performance Testing Results](#performance-testing-results)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
  - [Running the Application](#running-the-application)
- [Performance Testing](#performance-testing)
- [Technologies Used](#technologies-used)
- [Contributing](#contributing)
- [License](#license)

## Overview

This project showcases the difference in performance when running a Node.js server using:

1. A single process (default `npm start`)
2. Node.js Cluster module (`npm run start-cluster`)
3. PM2 process manager (`npm run start-pm2`)

## Features

- Demonstrates how Node.js clustering improves request handling by utilizing multiple CPU cores.
- Provides an easy-to-run load testing script (`test-load`) to evaluate performance.
- Highlights the impact of process management with PM2.

## Performance Testing Results

Below are the results of running the `test-load` script under different configurations:

### Single Process

- **Total time:** 11.148 seconds
- **Mean latency:** 2818.1 ms
- **Effective RPS:** 108

### Clustered Processes

- **Total time:** 3.746 seconds
- **Mean latency:** 997.6 ms
- **Effective RPS:** 320

### PM2 with Clustering

- **Total time:** 0.377 seconds
- **Mean latency:** 102.1 ms
- **Effective RPS:** 3183

> **Note:** Results may vary based on hardware and system configurations.

## Getting Started

Follow these instructions to set up and run the application locally.

### Running the Application

#### Single Process

Start the server using a single process:

```bash
npm start
```

#### Using Node.js Cluster

Run the application with clustering:

```bash
npm run cluster
```

#### Using PM2

Start the application with PM2 in cluster mode:

```bash
pm2 start index.js -i max
```

Check the PM2 logs to monitor activity:

```bash
pm2 logs
```

Stop the PM2 process:

```bash
pm2 stop all
```

## Performance Testing

The repository includes a simple load testing script (`test-load`) to measure performance. Run the script as follows:

```bash
npm run test-load
```

Compare results across the different modes (single process, cluster, PM2).

## Technologies Used

- **Node.js**: JavaScript runtime
- **Cluster Module**: Built-in Node.js module for creating child processes
- **PM2**: Advanced process manager for Node.js
- **Artillery**: Load testing tool (used in `test-load`)

## Contributing

Contributions are welcome! If you find any issues or have suggestions for improvements, please submit a pull request or open an issue.

## License

This project is licensed under the [MIT License](LICENSE).
