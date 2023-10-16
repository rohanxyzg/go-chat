# go-chat
A chat server in golang

# Project Setup

This README provides the steps to set up your local development environment for this project.

1. **Set Up a Local PostgreSQL Container Using Docker**: To create a local PostgreSQL container, run the following command:

    ```bash
    docker run --name postgres-chat -e POSTGRES_PASSWORD=your_password -p 5432:5432 -d postgres
    ```

    Replace `your_password` with your desired PostgreSQL password.

2. **Set Up the Database**:
   - Run the following commands to set up the database:

    ```bash
    make postgresinit
    make postgres
    make createdb
    ```

3. **Run the Server (go run main.go)**: Navigate to the server directory and start the server with the following command:

    ```bash
    go run main.go
    ```

    The server will be accessible at `http://localhost:8094`.

4. **Login**: Use the following `curl` command to log in with your email and password:

    ```bash
    curl --request POST \
      --url http://localhost:8094/login \
      --header 'Content-Type: application/json' \
      --data '{
        "email": "rohanxyz@gmail.com",
        "password": "323882"
      }'
    ```

5. **Create a Room**: To create a chat room, use the following `curl` command:

    ```bash
    curl --request POST \
      --url http://localhost:8094/ws/createRoom \
      --header 'Content-Type: application/json' \
      --data '{
        "id": "3",
        "name": "Rohan3"
      }'
    ```

    Adjust the `id` and `name` as needed for your chat room.

6. **Join the Room Using WebSocket**: Join a chat room by establishing a WebSocket connection with the following URL:

    ```
    ws://localhost:8094/ws/joinRoom/1?userId=1&username=user
    ```

    Replace `1`, `userId`, and `username` as per your requirements.

7. **Start Chatting!**: You're all set to start chatting in the joined room using the WebSocket connection.

Feel free to explore and further develop this project. Happy coding!
