## How To Setup CI/CD using Gitlab Actions

1. Create your project :)
2. Go to aws
3. Create EC2 instance
4. Connect to your ubuntu via your terminal
5. install node and pm2
6. sudo apt update && sudo apt upgrade -y
7. sudo apt update && sudo apt upgrade -y
8. curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash -
9. sudo apt install -y nodejs
10. sudo npm install -g pm2
11. ssh -i your-key.pem ubuntu@your-server-ip
12. sudo apt update
13. sudo apt install git -y
14. git clone https://github.com/your-username/your-repo.git
15. cd your-repo
16. git pull origin main
17. ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
18. cat ~/.ssh/id_rsa.pub
19. Copy that key into GitHub → Settings → SSH Keys.
20. In your repo → .github/workflows/deploy.yml:
name: Deploy to AWS
on:
  push:
    branches: ["main"]
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - name: SSH into AWS and deploy
        uses: appleboy/ssh-action@v0.1.10
        with:
          host: ${{ secrets.AWS_HOST }}
          username: ubuntu
          key: ${{ secrets.AWS_KEY }}
          script: |
            cd /home/ubuntu/test_cicd
            git pull origin main
            npm install --production
            pm2 start app.js
21. AWS_HOST → set it to your EC2 Public IP
22. AWS_KEY → paste your private key (the .pem file content).
23. Go to your repo on GitHub → Settings → Secrets and variables → Actions → New repository secret.
24. On ubuntu terminal from your terminal : git config --global --add safe.directory /home/ubuntu/test_cicd
25. sudo chown -R ubuntu:ubuntu /home/ubuntu/test_cicd
26. ll
27. cd test_cicd
28. ll
29. cat README.md
30. lsof -i :3020
31. Add server running port on security groups of instance
