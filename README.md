# Human-connect-
This is a simple calculator app built in Python on Replit. It allows users to perform basic arithmetic operations like addition, subtraction, multiplication, and division.
name: Node.js CI

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:
  build:

    runs-on: ubuntu-latest

    steps:
    - name: Checkout repository
      uses: actions/checkout@v4

    - name: Setup Node.js
      uses: actions/setup-node@v3
      with:
        node-version: '16'  # Specify the Node.js version you want to use

    - name: Install dependencies
      run: npm install

    - name: Run tests
      run: npm test

    - name: Deploy to Azure
      uses: azure/webapps-deploy@v2
      with:
        app-name: your-app-name
        slot-name: production
        publish-profile: ${{ secrets.AzureAppService_PublishProfile }}