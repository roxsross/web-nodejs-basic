---

# Running the Node.js Application Locally

This guide will walk you through the steps to run the Node.js application on your local machine.

## Prerequisites

Before starting, ensure you have the following installed on your system:

- Node.js: Download and install from [nodejs.org](https://nodejs.org/)
- Git: Download and install from [git-scm.com](https://git-scm.com/)

## Steps

1. **Clone the Repository:**

   Open your terminal and run the following command to clone the repository:

   ```bash
   git clone https://github.com/roxsross/web-nodejs-basic.git
   ```

2. **Navigate to the Project Directory:**

   Change into the project directory:

   ```bash
   cd basic_nodejs_webpage
   ```

3. **Install Dependencies:**

   Install the required dependencies using npm:

   ```bash
   npm install
   ```

4. **Run the Application:**

   Start the Node.js application:

   ```bash
   npm start
   ```

5. **Access the Application:**

   Once the application has started, open your web browser and go to:

   ```
   http://localhost:8081
   ```

   You should now see the Node.js application running locally on your machine.

6. **Stopping the Application:**

   To stop the application, press `Ctrl + C` in the terminal where the application is running.

## Additional Notes

- The application will be running on port 8081 by default. If you need to change the port, you can modify it in the `server.js` file.
- Make sure no other application is using port 8081 on your system before starting the Node.js application.

---

