1️⃣ Kubernetes Architecture & How It Works Under the Hood

Kubernetes architecture is based on two main parts:

🧠 1. Control Plane (The Brain)

This is where all decisions happen.

 Main components:
 
  API Server
    Entry point to Kubernetes
    You (or CI/CD) talk to it using kubectl
    
  Scheduler
    Decides which node will run your app (pod)
    
 Controller Manager
    Watches the system and fixes problems
    
Example: If a pod dies → it creates a new one.

etcd
  Database that stores cluster state
  Example: “I want 3 pods” → stored here
  
🏗️ 2. Worker Nodes (The Workers)

These are the machines that actually run your apps.

Components:

  kubelet
    Agent that talks to control plane
    Ensures containers are running
      
  Container Runtime
    Runs containers (like Docker)
    kube-proxy
    Handles networking between pods
    
🔁 How Kubernetes Works (Under the Hood Flow)

          You → kubectl → API Server → etcd (store desired state)
                                    ↓
                              Scheduler picks node
                                    ↓
                          kubelet runs container
                                    ↓
                   Controller keeps everything correct
                   
🧠 Key Concept (VERY IMPORTANT)

Kubernetes works on:

Desired State vs Current State

Example:

You say: “I want 3 pods”

Kubernetes checks:

If only 2 exist → creates 1 more

If 4 exist → deletes 1.
