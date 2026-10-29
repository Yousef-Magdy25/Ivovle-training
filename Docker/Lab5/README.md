# Lab 5: Docker Image Vulnerability Scanning with Trivy

## Objective
Scan a Docker image for security vulnerabilities using Trivy, review HIGH and CRITICAL findings, and reduce vulnerabilities by updating the base image and application dependencies.

## Tools Used
- Docker
- Trivy
- Node.js
- npm

## Steps Performed

### 1. Clone the Repository
```bash
git clone https://github.com/Ibrahim-Adel15/TrivyImage.git
cd TrivyImage
```

### 2. Build the Docker Image
```bash
docker build -t trivy-lab:v1 .
```

### 3. Install and Verify Trivy
Install Trivy using the official installation instructions, then verify it:

```bash
trivy --version
```

### 4. Scan the Docker Image
Scan the image for all vulnerabilities:

```bash
trivy image trivy-lab:v1
```

Scan only HIGH and CRITICAL vulnerabilities:

```bash
trivy image --severity HIGH,CRITICAL trivy-lab:v1
```

### 5. Generate an HTML Report
Download the official Trivy HTML template:

```bash
wget https://raw.githubusercontent.com/aquasecurity/trivy/main/contrib/html.tpl -O html.tpl
```

Generate the vulnerability report:

```bash
trivy image --format template --template "@html.tpl" --output trivy-report.html trivy-lab:v1
```

Generate a report containing only HIGH and CRITICAL findings:

```bash
trivy image --severity HIGH,CRITICAL --format template --template "@html.tpl" --output high-critical-report.html trivy-lab:v1
```

### 6. Remediate Vulnerabilities
- Updated the Docker base image from `node:18-bullseye` to `node:24-bookworm-slim`.
- Generated or updated `package-lock.json`.
- Reviewed application dependency vulnerabilities using `npm audit`.
- Applied available dependency fixes using `npm audit fix`.
- Rebuilt the image after making the changes.

### 7. Rebuild the Updated Image
```bash
docker build --no-cache -t ivolve-app:v2 .
```

### 8. Rescan the Updated Image
```bash
trivy image ivolve-app:v2
```

```bash
trivy image --severity HIGH,CRITICAL ivolve-app:v2
```

Generate the updated HTML report:

```bash
trivy image --severity HIGH,CRITICAL --format template --template "@html.tpl" --output ivolve-app-v2-high-critical.html ivolve-app:v2
```

## Results
- Built and scanned the initial Docker image.
- Identified vulnerabilities in operating system packages and Node.js dependencies.
- Updated the base image and application dependencies where fixes were available.
- Rebuilt the application image and rescanned it with Trivy.
- Generated HTML reports to review the remaining vulnerabilities.

