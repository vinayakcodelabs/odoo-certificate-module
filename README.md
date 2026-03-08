# Odoo Certificate Engine

A production-grade, multi-template certificate issuance and management engine for Odoo 16. This module provides a robust framework for designing, generating, and managing the lifecycle of certificates with QWeb PDF rendering and offline QR code verification.

# Odoo Certificate Printing Module

![Odoo 16](https://img.shields.io/badge/Odoo-16.0-%23A3478E)
![License](https://img.shields.io/badge/License-LGPL--3.0-blue)
![Python](https://img.shields.io/badge/Python-3.7%2B-green)
![GitHub](https://img.shields.io/github/stars/vinayakcodelabs/odoo-certificate-module)

## 🌟 Key Features

* **Five-Layer Architecture**: Clean separation of Template Definition, Paper Formats, Context Builder, QWeb Renderer, and Lifecycle Management.
* **Certificate Lifecycle Management**: Complete trace of certificate states (`Draft` -> `Submitted` -> `Issued` -> `Expired` / `Revoked`).
* **Offline QR Code Verification**: Automatically generated, offline-verifiable QR codes embedded directly into the issued certificates.
* **Rich Frontend Interface**: Custom backend widgets including an Admin Dashboard, Template Manager, and Paper Format Widget.
* **Automated Expiry Handling**: Built-in cron jobs to automatically transition expired certificates.
* **Dynamic Context Builder**: Advanced dynamic data fetching and expression parsing for certificate generation.
* **Vessel Pharmacy Integration**: Out-of-the-box support for specialized maritime/pharmacy certificate structures.

## 🏗️ Architecture

1. **Templates (`cert.template`)**: Define the content layout and structure using QWeb.
2. **Paper Formats (`cert.paper.format`)**: Precise control over page dimensions, margins, and DPI for printing.
3. **Context Builder (`cert.context.builder`)**: Gathers dynamic data, evaluates expressions, and feeds it to the renderer.
4. **Renderer (`cert.renderer`)**: Seamlessly compiles the template, context, and paper format into a high-quality PDF.
5. **Lifecycle & Instance (`cert.certificate`)**: Manages the instances, approval workflows, and validity periods.

## 🛠️ Technical Specifications

* **Odoo Version**: 16.0.1.0.0
* **License**: LGPL-3
* **Dependencies**: `base`, `mail`, `hr`, `stock`, `web`
* **Python Dependencies**: `qrcode` (Must be installed via `pip install qrcode`)

## 🚀 Installation

1. Ensure the required Python dependencies are installed on your Odoo server:
   ```bash
   pip3 install qrcode
   ```
2. Clone or download the repository into your Odoo `custom-addons` directory (or clone from the source):
   ```bash
   git clone https://github.com/vinayakcodelabs/odoo-certificate-module.git certificate_engine
   ```
3. Update the app list in your Odoo instance with Developer Mode enabled (**Apps > Update Apps List**).
4. Search for **Certificate Manager** and click **Install**.

## 💻 Usage

### 1. Creating a Template
Navigate to **Certificates > Configuration > Templates** to design a new certificate layout using QWeb syntax.

### 2. Defining Paper Formats
Navigate to **Certificates > Configuration > Paper Formats** to adjust the dimensions, margins, and layout to perfectly match your specific PDF or physical printing requirements.

### 3. Issuing a Certificate
- Go to **Certificates > Certificates**.
- Create a new Certificate, assign a template, and fill in the necessary details (e.g., Trainee details, issue/expiry dates).
- Submit the certificate for manager review using the **Submit** workflow.
- An authorized Certificate Manager can review and click **Issue**.
- Upon issuance, a unique sequence number and QR code are automatically generated, and the finalized PDF is rendered and attached.

## 🛡️ Security & Access Rights

The module implements strict record rules and access control lists (`cert_security_groups.xml`). It separates standard users from **Certificate Managers** who possess the authority to approve, issue, or revoke certificates.

## 👨‍💻 Author

* **Vinayak Murali**
* **Repository**: [odoo-certificate-module](https://github.com/vinayakcodelabs/odoo-certificate-module.git)
