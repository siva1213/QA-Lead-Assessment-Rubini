<h2>Part 5 - Answers</h2>

**1. Create a simple CI pipeline using GitHub Actions to run your Playwright or API tests**
I have created CI pipeline using Github actions for Playwright automation project & I have shared a video clip for the explanation under https://drive.google.com/drive/u/0/folders/18eIqYoIZGcaFbZyPYssANroziLHqCeC6.

**2. Write a Java/TypeScript class for a customtest reporting mechanism**
I have already added reporters/CustomReporter.ts in the Playwright web automation project in https://github.com/siva1213/QA-Lead-Assessment-Sivarubini

**3. Create a shell script to automate test environment setup**
Added shell script below to automate test environment for Playwright test automation projects.

#!/bin/bash

# Exit on error
set -e

echo "=== Setting up Playwright Test Environment ==="

# Step 1: Install Node.js dependencies
if [ -f package.json ]; then
    echo "Installing Node.js dependencies..."
    npm install
else
    echo "No package.json found. Initialize a Node.js project first."
    exit 1
fi

# Step 2: Install Playwright and Browsers
if ! npx playwright --version &>/dev/null; then
    echo "Installing Playwright..."
    npm install -D @playwright/test
fi

echo "Installing Playwright browsers..."
npx playwright install

# Optional: Run tests
echo "Running tests..."
npx playwright test

echo "=== Test Environment Setup Complete ==="
