# chessx
A simple design of a chess application that I made mostly from scratch, using the chess.js library for functionality.

## For help or more information about this one man project don't hesitate to reach out!

I deployed this app to heroku from where I linked my own domain to it: https://chessx.dev

# here is a basic example of how to deploy it:

Sure! Here is a detailed example of how to deploy an application to Heroku and add your custom domain to it:

### Step 1: Set Up Your Heroku Account

1. **Sign Up for Heroku**:
   - Go to [Heroku](https://www.heroku.com/) and sign up for a free account if you don't already have one.

2. **Install the Heroku CLI**:
   - Download and install the [Heroku CLI](https://devcenter.heroku.com/articles/heroku-cli).
   - Verify the installation by running:
     ```bash
     heroku --version
     ```

### Step 2: Prepare Your Application

1. **Create Your Application**:
   - If you already have a project, navigate to its root directory. If not, create a new one. Here’s an example with a simple Node.js application:
     ```bash
     mkdir myapp
     cd myapp
     npm init -y
     npm install express
     ```
   - Create a `server.js` file with the following content:
     ```javascript
     const express = require('express');
     const app = express();
     const PORT = process.env.PORT || 3000;

     app.get('/', (req, res) => {
       res.send('Hello, Heroku!');
     });

     app.listen(PORT, () => {
       console.log(`Server is running on port ${PORT}`);
     });
     ```

2. **Create a `Procfile`**:
   - Create a file named `Procfile` in the root of your project directory with the following content:
     ```txt
     web: node server.js
     ```

3. **Create a `package.json` File**:
   - Make sure your `package.json` file includes a start script:
     ```json
     "scripts": {
       "start": "node server.js"
     }
     ```

4. **Initialize a Git Repository**:
   - Initialize a Git repository and commit your code:
     ```bash
     git init
     git add .
     git commit -m "Initial commit"
     ```

### Step 3: Deploy to Heroku

1. **Login to Heroku**:
   - Login to your Heroku account using the CLI:
     ```bash
     heroku login
     ```

2. **Create a New Heroku Application**:
   - Create a new Heroku application:
     ```bash
     heroku create myapp
     ```
   - Replace `myapp` with your desired application name.

3. **Deploy Your Code**:
   - Deploy your application to Heroku:
     ```bash
     git push heroku main
     ```

4. **Open Your Application**:
   - Open your newly deployed application in your browser:
     ```bash
     heroku open
     ```

### Step 4: Add Your Custom Domain

1. **Add a Custom Domain in Heroku Dashboard**:
   - Go to your [Heroku Dashboard](https://dashboard.heroku.com/) and select your application.
   - Navigate to the “Settings” tab.
   - Scroll down to the “Domains” section and click “Add domain.”
   - Enter your custom domain (e.g., `www.yourdomain.com`) and click “Next.”

2. **Configure DNS Settings**:
   - Note the DNS target provided by Heroku (e.g., `myapp.herokuapp.com`).
   - Log in to your domain registrar (e.g., Namecheap) and navigate to the DNS settings for your domain.
   - Create a CNAME record pointing your custom domain to the Heroku DNS target. For example:
     - **Host**: `www`
     - **Type**: `CNAME`
     - **Value**: `myapp.herokuapp.com`

3. **Verify Domain**:
   - After configuring the DNS settings, return to the Heroku Dashboard and click “Finish.”
   - It may take some time for DNS changes to propagate. You can use tools like [DNS Checker](https://dnschecker.org/) to check the status.

4. **Update Application for Root Domain (Optional)**:
   - If you want your application to be accessible from the root domain (e.g., `yourdomain.com`), you might need to add an A record:
     - **Host**: `@`
     - **Type**: `A`
     - **Value**: Use Heroku's IP addresses (find them [here](https://devcenter.heroku.com/articles/custom-domains#dns-targets))

### Step 5: SSL Configuration (Optional)

1. **Automatic SSL (Recommended)**:
   - Heroku provides free automatic SSL for custom domains. Ensure your domain has been verified and Heroku will provision an SSL certificate for you.
   - In the Heroku Dashboard, go to the “Settings” tab, and under “Domains,” you should see your custom domain with SSL enabled.

2. **Manual SSL Configuration**:
   - If you prefer manual configuration, you can follow the steps provided in the [Heroku SSL documentation](https://devcenter.heroku.com/articles/ssl).

That’s it! Your application is now deployed to Heroku and accessible via your custom domain.
