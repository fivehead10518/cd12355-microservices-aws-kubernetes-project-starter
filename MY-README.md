## Project Instructions
1. Set up a Postgres database with a Helm Chart
2. Create a `Dockerfile` for the Python application. Use a base image that is Python-based.
3. Write a simple build pipeline with AWS CodeBuild to build and push a Docker image into AWS ECR
4. Create a service and deployment using Kubernetes configuration files to deploy the application
5. Check AWS CloudWatch for application logs

### Deliverables
1. Dockerfile
`analytics/Dockerfile`

2. Screenshot of AWS CodeBuild pipeline
![alt text](<screenshots/image copy 2.png>)

3. Screenshot of AWS ECR repository for the application's repository
![alt text](<screenshots/image copy 3.png>)

4. Screenshot of `kubectl get svc` (ACHTUNG ANALYTICS FEHLT NOCH)
![alt text](<screenshots/Screenshot 2026-09-21 222654.png>)
![alt text](<screenshots/image copy 4.png>)

5. Screenshot of `kubectl get pods` (NACHTRAG NACH DEPLOYMENT)
![alt text](<screenshots/image copy 6.png>)

6. Screenshot of `kubectl describe svc <DATABASE_SERVICE_NAME>`
![alt text](<screenshots/image copy.png>)

7. Screenshot of `kubectl describe deployment <SERVICE_NAME>`
![alt text](<screenshots/image copy 7.png>)

8. All Kubernetes config files used for deployment (ie YAML files)
9. Screenshot of AWS CloudWatch logs for the application
10. `README.md` file in your solution that serves as documentation for your user to detail how your deployment process works and how the user can deploy changes. The details should not simply rehash what you have done on a step by step basis. Instead, it should help an experienced software developer understand the technologies and tools in the build and deploy process as well as provide them insight into how they would release new builds.

## Initialize the database with the following command:

```bash
export DB_PASSWORD=mypassword

for file in $(ls -1v db/*.sql); do
  echo "==> Seeding: $file"
  PGPASSWORD="$DB_PASSWORD" psql --host 127.0.0.1 -U myuser -d mydatabase -p 5433 < "$file"
done
```


### Stand Out Suggestions
Please provide up to 3 sentences for each suggestion. Additional content in your submission from the standout suggestions do _not_ impact the length of your total submission.
1. Specify reasonable Memory and CPU allocation in the Kubernetes deployment configuration
2. In your README, specify what AWS instance type would be best used for the application? Why?
3. In your README, provide your thoughts on how we can save on costs?