---
title: "Boost Your CI Workflow: A Guide to Integrating Jenkins and Robot Framework for Web and API Testing"
date: 2023-07-25
draft: true
---




## Setup step-by-step
### Robot Framework install


Detailed step-by-step installation/setup process.
### Part 1: Install Jenkins

1. **Update your system:** First, make sure your system is up-to-date by running `sudo apt update && sudo apt upgrade` in Terminal.

2. **Install Java:** Jenkins requires Java to run. Install Java Development Kit (JDK) using the command: `sudo apt install openjdk-11-jdk`.

3. **Add the Jenkins Debian repository:** Add the Jenkins key and source list using the following commands:

```bash
curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key | sudo tee \
  /usr/share/keyrings/jenkins-keyring.asc > /dev/null
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null

```

4. **Install Jenkins:** Update your local package index and then install Jenkins by running `sudo apt update` followed by `sudo apt install jenkins`.

5. **Start Jenkins:** Now, start the Jenkins service using `sudo systemctl start jenkins`.

6. **Enable Jenkins to start at system boot:** You can make Jenkins start up whenever your system boots by using `sudo systemctl enable jenkins`.

### Part 2: Setup Jenkins

1. **Initial setup:** In your browser, navigate to http://localhost:8080. You will see a setup wizard.

2. **Unlock Jenkins:** Retrieve the auto-generated administrative password using `sudo cat /var/lib/jenkins/secrets/initialAdminPassword`. Copy and paste this password into the Jenkins setup wizard and click "Continue".

3. **Customize Jenkins:** Select "Install suggested plugins" to install the recommended set of plugins, which are based on most common use cases.

4. **Create an Admin User:** You'll be prompted to create your first admin user. Enter the desired username, password, full name, and email, then click "Save and Continue".

5. **Instance Configuration:** Confirm the preferred URL for Jenkins, then click "Save and Finish".

6. **Setup Complete:** Click "Start using Jenkins" to complete the setup.

**Part 3: Install Robot Framework Plugin**

1. **Manage Plugins:** Navigate to "Manage Jenkins" > "Manage Plugins" > "Available". 

2. **Search for Robot Framework plugin:** Use the filter bar to find "Robot Framework plugin", select it, and click "Install without restart".

**Part 4: Configure Jenkins Job**

1. **Create a new job:** Click "New Item" from the Jenkins dashboard.

2. **Job details:** Enter a name for the job, select "Freestyle project", and click "OK".

3. **Source Code Management:** As we are using a local directory, you can leave this section empty.

4. **Build Triggers:** If you want the tests to run periodically, you can set it up here using "Build periodically" and specifying the schedule in cron format.

5. **Build Environment:** Configure the environment necessary for your tests.

6. **Build:** In the Build section, select "Add build step" > "Execute shell". Enter the command to run your Robot Framework tests. Assuming you've navigated to the directory containing the tests, it would look something like this: `robot -d results tests/`.

7. **Post-build Actions:** In the Post-build Actions section, select "Add post-build action" > "Publish Robot Framework test results". In the "Robot results" field, specify the location of the results (e.g., `results/output.xml`).

8. **Save and run:** Click "Save". Now, to run your job, click "Build Now" on the job page.

Remember, the `robot -d results tests/` command assumes your test files are in a directory named 'tests/' in your Jenkins workspace and that the results will be stored in a directory named 'results/'. Adjust these paths as necessary based on your actual directory structure.

With this setup, you now have a Jenkins job configured to run your local Robot Framework tests. Jenkins will execute the tests whenever the job is triggered and display the results in a user-friendly manner thanks to the Robot Framework plugin.






Yes, in order to run Robot Framework tests, the machine where Jenkins server runs (be it your local machine or a remote server) needs to have both Python and Robot Framework installed. Here's a step-by-step guide to install them:

**Step 1: Install Python**

If you don't already have Python installed, you can do so by running the following commands in the terminal:

```bash
sudo apt update
sudo apt install python3
sudo apt install python3-pip
```

sudo apt update && sudo apt install python3 && sudo apt install python3-pip

You can confirm the installation by checking the version of Python and pip:

```bash
python3 --version
pip3 --version
```

**Step 2: Install Robot Framework**

Once Python and pip are installed, you can install Robot Framework using pip:

```bash
pip3 install robotframework
```

You can confirm the installation of Robot Framework by checking its version:

```bash
robot --version
```

**Step 3: Install SeleniumLibrary**

In order to interact with web browsers, you'll also need to install SeleniumLibrary:

```bash
pip3 install robotframework-seleniumlibrary
```

**Step 4: Install WebDriver & google-chrome**

sudo apt install unzip

wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb

sudo dpkg -i google-chrome-stable_current_amd64.deb

sudo apt-get install -f

sudo dpkg -i google-chrome-stable_current_amd64.deb

Lastly, install the appropriate WebDriver for the browser you want to use for testing. If you're using Chrome, you would need to install ChromeDriver. Here is how you can install it:

```bash
wget https://chromedriver.storage.googleapis.com/2.41/chromedriver_linux64.zip
unzip chromedriver_linux64.zip
sudo mv chromedriver /usr/bin/chromedriver
sudo chown root:root /usr/bin/chromedriver
sudo chmod +x /usr/bin/chromedriver
```

Please note that the above command will download a specific version of ChromeDriver. You should replace the URL with the download link for the latest version that matches your installed version of Chrome. You can find this link on the [ChromeDriver download page](https://sites.google.com/a/chromium.org/chromedriver/downloads).

Once you've completed these steps, your Jenkins server should be able to execute Robot Framework tests.








