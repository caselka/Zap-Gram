# ZapGram
ZapGram is a serverless, high-speed Telegram bot deployed on AWS Lambda using Terraform and Git Bash. Inspired by the speed of a lightning zap, ZapGram delivers instant responses, automates tasks, and seamlessly integrates with the Telegram API for a smooth user experience.
# ⚡ ZapGram – The Lightning-Fast Telegram Bot  

ZapGram is a **serverless, high-speed Telegram bot** deployed on **AWS Lambda** using **Terraform** and **Git Bash**. Inspired by the **speed of a lightning zap**, ZapGram delivers instant responses, automates tasks, and seamlessly integrates with the **Telegram API** for a smooth user experience.  

> Lightning-fast responses, powered by the cloud! ⚡  

---

## 🚀 Features  
✅ **Instant Deployment** – Fully automated with Git Bash & Terraform  
✅ **Serverless & Cost-Effective** – Runs on AWS Lambda  
✅ **Auto Webhook Registration** – Connects to Telegram API automatically  
✅ **Secure Environment Handling** – Uses `.env` for API keys  
✅ **Easy Updates** – Modify and redeploy in seconds  

---

## 📌 Prerequisites  

Ensure you have the following installed:  

- **Git Bash** → [Download](https://git-scm.com/downloads)  
- **AWS CLI** → [Download](https://awscli.amazonaws.com/AWSCLIV2.msi)  
- **Terraform** → [Download](https://developer.hashicorp.com/terraform/downloads)  
- **Python** (3.x) → [Download](https://www.python.org/downloads/)  
- **Required Python Libraries**:  

```bash
  pip install boto3 python-telegram-bot schedule requests
```

🔧 Setup Guide

1️⃣ Clone the Repository
```bash
git clone https://github.com/YOUR_GITHUB_USERNAME/zapgram.git
cd zapgram
```
2️⃣ Set Up Environment Variables
Create a .env file to store sensitive data:

```bash
echo 'export TELEGRAM_BOT_TOKEN="your_bot_token_here"' > .env
```
Then, load the environment variables:
```bash
source .env
```
3️⃣ Deploy the Bot
Run the deployment script:

```bash
bash deploy.sh
```
This will:
✅ Package the bot
✅ Deploy AWS infrastructure
✅ Retrieve the API Gateway URL
✅ Register the Telegram webhook

---

4️⃣ Update the Bot Without Full Redeployment
If you update lambda_function.py, run:

```bash
zip -r telegram_bot.zip lambda_function.py
aws lambda update-function-code --function-name zapgram_bot --zip-file fileb://telegram_bot.zip
```
---

🏗 Infrastructure Created by Terraform

AWS Lambda – Runs the bot

API Gateway – Handles Telegram webhook requests

IAM Role – Provides necessary permissions

CloudWatch Logs – Stores bot logs

---

📄 Project Structure
```bash
/zapgram
│── lambda_function.py      # Telegram bot logic
│── deploy.sh               # Automated deployment script
│── main.tf                 # Terraform configuration
│── .env                    # Environment variables (not committed)
│── README.md               # This guide
```
---

🤖 Bot Logic (lambda_function.py)

ZapGram is built using python-telegram-bot and can be modified inside lambda_function.py to include more features.

---

🔥 Next Steps
🔹 Deploy multiple bots with different API keys
🔹 Store user interactions in DynamoDB
🔹 Extend bot functionality with more commands

---

🛠 Troubleshooting

Terraform Apply Fails?
Try running:

```bash
terraform destroy -auto-approve
terraform apply -auto-approve
```
Lambda Function Not Updating?

Use:

```bash
aws lambda update-function-code --function-name zapgram_bot --zip-file fileb://telegram_bot.zip
```

---

📜 License

This project is open-source under the MIT License. Feel free to use and modify it!
