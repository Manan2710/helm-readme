# Boomi Atom and Gateway Helm Chart

This repository contains a Helm chart for deploying **Boomi Atom** and **Boomi Gateway** on a Kubernetes cluster.

## Fork and Clone the Repository

### 1. Fork the Repository

To contribute or customize the chart, first fork this repository by clicking the "Fork" button in the top-right corner of this page.

### 2. Clone Your Fork

Once you've forked the repository, clone it to your local machine using the following command:

```bash
git clone https://github.com/<your-username>/<your-forked-repo>.git
```
Replace <your-username> with your GitHub username and <your-forked-repo> with the name of your forked repository.

Navigate into the cloned directory:

```bash
cd <your-forked-repo>
```

## Installation

### 1. Set the Required Values

Before installing, you need to configure the following values:
- `INSTALL_TOKEN`: Your Boomi installation token
  - For **Boomi Atom**, the token should start with `atom`
  - For **Boomi Gateway**, the token should start with `gateway`
- `BOOMI_ACCOUNTID`: Your Boomi account ID
- `BOOMI_ENVIRONMENTID`: The Boomi environment where the Atom and Gateway will be deployed

You can set these values in a custom values file (e.g., `values.yaml`):

```yaml
INSTALL_TOKEN: "<your_install_token>"
BOOMI_ACCOUNTID: "<your_boomi_accountid>"
BOOMI_ENVIRONMENTID: "<your_boomi_environment>"
```
#### Example for Boomi Atom:
```yaml
INSTALL_TOKEN: "atom-xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"
BOOMI_ACCOUNTID: "12345"
BOOMI_ENVIRONMENTID: "env-12345"
```
#### Example for Boomi Gateway:
```yaml
INSTALL_TOKEN: "gateway-xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"
BOOMI_ACCOUNTID: "12345"
BOOMI_ENVIRONMENTID: "env-12345"
```

### 2. Create a Namespace (Optional)

If your Helm chart does not include namespace configuration, you can create the namespace separately.


```bash
kubectl create namespace <namespace-name>
``` 

Example:
To create a namespace called `uat`, run:

```bash
kubectl create namespace uat
```

#### Verify the Namespace

To check if the uat namespace has been created, run:

```bash
kubectl get namespaces
```
This will display a list of namespaces, and uat should appear in the list:

Example Output:
```bash
NAME              STATUS    AGE
default           Active    10d
kube-node-lease   Active    10d
kube-public       Active    10d
kube-system       Active    10d
uat               Active    5s
```
### 3. Install the Helm Chart

Run the following command to install the Helm chart:

```bash
helm install <release-name> <path-to-chart-directory>
```

Replace:
- `<release-name>` with a name for the release
- `<path-to-chart-directory>` with the path to the Helm chart directory

### 4. Verify the Installation

To check if the Helm chart was installed successfully, run:

```bash
helm list --all
```

To check the status of the pods in your Kubernetes cluster, run:

```bash
kubectl get po -A
```