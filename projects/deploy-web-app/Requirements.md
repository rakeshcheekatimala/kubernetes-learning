# Project: Deploy and Expose a Web App

You are a DevOps engineer at esc bash. A developer has an app packaged as a container image and needs it running on Kubernetes: several copies for reliability, reachable at a stable in-cluster address, and able to heal itself if a pod dies. That is your job here.

## The app

The app is the small public image `hashicorp/http-echo:latest`. It is a tiny web server that replies with a fixed message. You configure the message and the port it listens on through its container arguments:

```yaml
args: ["-text=esc bash orders", "-listen=:5678"]
```

The container listens on port **5678** and answers every request with **esc bash orders**.

## What to build

Work with manifests under `/root` and apply them. Produce the following.

### Deployment `orders`

- 3 replicas
- Pod template labelled `app: orders`
- One container using image `hashicorp/http-echo:latest`
- Container args set so it serves the text `esc bash orders` and listens on port `5678` (as shown above)

### Service `orders`

- Type `ClusterIP`
- Selector `app: orders`
- Port `80`, forwarding to the container's target port `5678`

## Done when

- The Deployment shows 3 ready replicas
- The Service has the pods behind it
- A request to `http://orders` from inside the cluster returns `esc bash orders`

## Concepts already covered

Everything here you have already done:

- Deployments and replicas — Deployments and Scaling
- Labels and selectors — Labels
- ClusterIP Services and in-cluster reachability — Services
