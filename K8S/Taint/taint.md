This document explains how taints and tolerations work in Kubernetes, with practical examples.

🧠 What Are Taints?
A taint is applied to a node.

It tells Kubernetes not to schedule any pods on this node unless those pods tolerate the taint.

📌 Syntax:

bash
Copy
Edit
kubectl taint nodes <node-name> key=value:effect
🔸 Example:

bash
Copy
Edit
kubectl taint nodes node01 dedicated=nginx:NoSchedule
This command prevents any pod from being scheduled on node01 unless the pod has a matching toleration.

🎯 What Are Tolerations?
A toleration is applied to a pod.

It allows the pod to be scheduled on nodes that have matching taints.

📌 Example toleration in a Pod/Deployment:

yaml
Copy
Edit
tolerations:
  - key: "dedicated"
    operator: "Equal"
    value: "nginx"
    effect: "NoSchedule"
This toleration matches the taint dedicated=nginx:NoSchedule.
