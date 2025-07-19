# Multithread-WebServer in JAVA

A simple Java web server implementation demonstrating both multi-threaded and thread pool approaches for handling multiple client connections concurrently.

## Features

- Accepts multiple client connections using either:
  - A new thread per client (see [`MultiThreaded/Server.java`](MultiThreaded-WebServer/MultiThreaded/Server.java))
  - A fixed-size thread pool (see [`ThreadPool/Server.java`](Multithread-WebServer/ThreadPool/Server.java))
- Responds to each client with a greeting message
- Example client code included for testing

## Project Structure

```
Multithread-WebServer/
├── MultiThreaded/
│   ├── Server.java
│   └── Client.java
├── ThreadPool/
│   └── Server.java
```

## How to Run

### 1. Compile the Server and Client

```sh
javac MultiThreaded/Server.java
javac MultiThreaded/Client.java
javac ThreadPool/Server.java
```

### 2. Start the Server

- For thread-per-client model:
  ```sh
  java MultiThreaded.Server
  ```
- For thread pool model:
  ```sh
  java ThreadPool.Server
  ```

### 3. Run the Client

In a separate terminal, run:
```sh
java MultiThreaded.Client
```

## Configuration

- The server listens on port `9901` by default.
- The thread pool size can be adjusted in [`ThreadPool/Server.java`](Multithread-WebServer/ThreadPool/Server.java) via the `poolSize` variable.

## Example Output

```
Server is listening on port 9901
Hello from server /127.0.0.1
```

## Load Testing with JMeter

You can use [Apache JMeter](https://jmeter.apache.org/) to test the performance and concurrency of this server.

### Steps:

1. **Download and install JMeter** from [here](https://jmeter.apache.org/download_jmeter.cgi).
2. **Start your server** (thread-per-client or thread pool model).
3. **Open JMeter** and create a new test plan:
    - Add a **Thread Group** (set number of users/threads and loop count).
    - Add a **TCP Sampler**:
        - Set the server’s IP (usually `localhost`) and port (`9901`).
        - Set the message to send (e.g., `Hello from client`).
    - Add a **Listener** (e.g., View Results Tree) to see responses.
4. **Run the test** and observe how your server handles multiple concurrent connections.

This helps you benchmark and analyze the scalability of your multithreaded server.

## License

This project is for educational purposes.