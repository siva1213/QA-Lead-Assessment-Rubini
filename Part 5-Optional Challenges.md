# Part 5 - Answers

**1. Create a simple CI pipeline using GitHub Actions to run your Playwright or API tests**
I have created CI pipeline using Github actions for Playwright automation project & I have shared a video clip for the explanation under https://drive.google.com/drive/u/0/folders/18eIqYoIZGcaFbZyPYssANroziLHqCeC6.

**2. Write a Java/TypeScript class for a customtest reporting mechanism**
I have already added reporters/CustomReporter.ts in the Playwright web automation project in https://github.com/siva1213/QA-Lead-Assessment-Sivarubini

**3. Create a shell script to automate test environment setup**
Added shell script below to automate test environment for Playwright test automation projects.

#!/bin/bash<br>

#Exit on error<br>
set -e<br>

echo "=== Setting up Playwright Test Environment ==="<br>

#Step 1: Install Node.js dependencies<br>
if [ -f package.json ]; then<br>
    echo "Installing Node.js dependencies..."<br>
    npm install<br>
else<br>
    echo "No package.json found. Initialize a Node.js project first."<br>
    exit 1<br>
fi<br>

#Step 2: Install Playwright and Browsers<br>
if ! npx playwright --version &>/dev/null; then<br>
    echo "Installing Playwright..."<br>
    npm install -D @playwright/test<br>
fi<br>

echo "Installing Playwright browsers..."<br>
npx playwright install<br>

#Optional: Run tests<br>
echo "Running tests..."<br>
npx playwright test<br>

echo "=== Test Environment Setup Complete ==="<br>
