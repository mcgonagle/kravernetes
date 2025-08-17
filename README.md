## Kravernetes - Full Contact Kubernetes
Krav means contact in Hebrew. Full contact k8s is an approach to k8s that focuses on practical real-world skills via the application of Krav Maga self-defense principles.

---

### History of Krav Maga

Krav Maga is a military self-defence and fighting system developed for the Israel Defense Forces (IDF) and Israeli security forces derived from a combination of techniques sourced from Boxing, Wrestling, Judo, Aikido, and Karate. Krav Maga is known for its focus on real-world situations and its extreme efficiency. It was derived from the street-fighting experience of Hungarian-Israeli martial artist Imi Lichtenfeld, who made use of his training as a boxer and wrestler, while defending the Jewish quarter against fascist groups in Bratislava, Czechoslovakia, during the mid-to-late 1930s. In the late 1940s, after his aliyah to Mandatory Palestine, he began to provide lessons on combat training to what was to become the IDF.

**Krav Maga has a philosophy emphasizing aggression, and simultaneous defensive and offensive maneuvers.** 

Some of the key focus is instinctive response under stress. To that end, Krav Maga is an eclectic system that has not sought to replace existing effective techniques, taking what is useful from available systems, for example:

    * Strikes – as per karate, and boxing,
    * Take-downs and throws – per judo, aikido and wrestling
    * Ground work – per judo and wrestling
    * Escapes from chokes and holds – per judo, aikido, wrestling
    * Empty-hand weapon defenses – per aikido

[DevSecOps]([https://share.getcloudapp.com/04uA24k9](https://capture.dropbox.com/D2MZoSvqoIO6RyXy)) is an eccelctic system as well.

### DevSecOps
@mcgonagle DevSecOps Definition - Shifting Security Left through a Technical and Cultural Focus on Teamwork and the Secure Delivery of Software Mission.  


> The purpose of *DevSecOps* is to integrate security controls and processes into the DevOps software development cycle, a process which is achieved by promoting the collaboration between security teams, development teams and operations teams.

Kraverenetes is a practical *DevSecOps* methodology which focuses on the four pillars of Krav Maga, which are:

    1. awareness
    2. avoidance
    3. de-escalation and escape
    4. last-resort decisive, simultaneous attack and defense


---

### Attack and Defense - Kravernetes Tenents
    1. Be aggressive but smart in your problem solving.
    2. Be vigilant in identifing and addressing challenges.
    3. Be proactive based on your current weaknesses or vulnerabilities; react quickly when you have to.
    4. Be tool agnostic.
    5. Invoke precision when executing tasks.
    6. Employ simple and repeatable techniques.
    7. Include situational awareness in all aspects of your practice.
    8. Understand the impact of stress on your planning and response.

**1. Be aggressive but smart in your problem solving**
- Use `kubectl delete --force --grace-period=0` when pods are stuck, but understand the consequences
- Implement circuit breakers and fail-fast patterns in your applications
- Scale aggressively during incidents: `kubectl scale deployment/app --replicas=20`

**2. Be vigilant in identifying and addressing challenges**
- Monitor continuously: `kubectl get events --watch --all-namespaces`
- Set up alerts for pod restarts, memory/CPU spikes, and failed deployments
- Implement health checks: readiness, liveness, and startup probes on every container

**3. Be proactive based on your current weaknesses; react quickly when you have to**
- Run `kube-bench` and `kubesec` regularly to identify security gaps
- Practice incident response with chaos engineering (Chaos Monkey, Litmus)
- Keep rollback commands ready: `kubectl rollout undo deployment/app`

**4. Be tool agnostic**
- Master both `kubectl` and alternative tools (k9s, lens, stern)
- Know multiple deployment methods: kubectl, Helm, Kustomize, ArgoCD
- Use different monitoring stacks: Prometheus+Grafana, ELK, Jaeger

**5. Invoke precision when executing tasks**
- Use specific selectors: `kubectl delete pods -l app=nginx,version=v1.2.3`
- Apply resource limits and requests to every container
- Use namespaces and RBAC with minimal required permissions

**6. Employ simple and repeatable techniques**
- Standardize on Helm charts or Kustomize overlays
- Use GitOps workflows for all deployments
- Create runbooks for common operations and incidents

**7. Include situational awareness in all aspects of your practice**
- Always check cluster state: `kubectl cluster-info` and `kubectl get nodes`
- Understand resource consumption: `kubectl top nodes` and `kubectl top pods`
- Monitor network policies and pod security contexts

**8. Understand the impact of stress on your planning and response**
- Practice deployments and rollbacks in staging environments
- Use feature flags to reduce deployment stress
- Implement gradual rollouts and blue-green deployments
    


---

### Retzev - "Continuous Motion" in Kubernetes

Retzev in Kravernetes means maintaining continuous, flowing operations that seamlessly combine defensive security measures with offensive optimization techniques. Like in Krav Maga, you never stop moving - each action flows into the next.

**Continuous Motion Examples:**

**Security Scanning → Remediation → Validation:**
```bash
# Flow from discovery to action
kube-bench run → kubectl apply -f security-policy.yaml → kubesec scan deployment.yaml
```

**Monitoring → Alerting → Auto-scaling → Optimization:**
```bash
# Metrics trigger scaling which triggers optimization
kubectl top nodes → HPA triggers → kubectl scale → Resource optimization
```

**Deploy → Test → Monitor → Rollback/Forward:**
```bash
# Deployment flows immediately into verification
kubectl apply -f app.yaml && kubectl rollout status deployment/app && curl health-check || kubectl rollout undo deployment/app
```

**Incident Response Chain:**
```bash
# Immediate response flows through investigation to resolution
kubectl describe pod → kubectl logs → kubectl exec -it → kubectl patch/delete
```

**GitOps Continuous Flow:**
```
Git commit → CI/CD pipeline → Deployment → Health checks → Prometheus metrics → Alert → Auto-remediation → Git commit
```

The key is never stopping - each Kubernetes action should trigger the next logical step in an unbroken chain of defensive and offensive operations.

--- 

### Situational Awareness = Kubernetes Mindfulness
Situation awareness in Kubernetes is the foundation for successful cluster operations and incident response. Like in combat situations, lacking awareness leads to critical failures, security breaches, and service outages.

**Kubernetes Awareness Levels:**

**-6 Unaware:** No monitoring, no alerts, deployments without resource limits
- Running workloads without knowing cluster capacity
- No logging or metrics collection
- Manual deployments without version control

**-5 Semi-Aware:** Basic monitoring but no proactive alerting
- Using `kubectl get pods` occasionally
- Some resource limits but no requests defined
- Reactive troubleshooting only

**-3 Aware:** Regular monitoring with basic alerts
- `kubectl top nodes/pods` checks during business hours
- CPU/Memory alerts configured
- Basic health checks implemented

**-2 Cautious:** Proactive monitoring with comprehensive alerting
- 24/7 monitoring with PagerDuty/Slack integration
- SLI/SLO tracking with error budgets
- Regular security scans and vulnerability assessments

**-1 Alert:** Advanced observability with predictive capabilities
- Distributed tracing with Jaeger/Zipkin
- Advanced metrics (RED/USE methods)
- Chaos engineering and failure injection testing

**0 Prepared:** Full spectrum awareness with automated response
- Machine learning-based anomaly detection
- Automated remediation for common failures
- Complete GitOps with policy-as-code enforcement
- Real-time security threat detection and response


---

### Kubernetes THREAT Model
**T** - Technical Threats  
**H** - Human Threats  
**R** - Resource Threats  
**E** - Environmental Threats  
**A** - Application Threats  
**T** - Trust Threats  

**Technical Threats:**
- Container escape vulnerabilities (CVE exploits)
- Privilege escalation through misconfigured RBAC
- Insecure container images with known vulnerabilities
- Unpatched Kubernetes control plane components
- Network policy bypasses and lateral movement

**Human Threats:**
- Insider threats with excessive cluster permissions
- Social engineering attacks targeting credentials
- Accidental misconfigurations by operators
- Insufficient security training and awareness
- Credential theft and account compromise

**Resource Threats:**
- Resource exhaustion attacks (CPU/Memory bombs)
- Storage attacks and persistent volume corruption
- Network bandwidth exhaustion (DDoS)
- Node capacity limits and cluster scaling failures
- Cost-based attacks inflating cloud bills

**Environmental Threats:**
- Cloud provider outages and availability zone failures
- Network partitions and split-brain scenarios
- Hardware failures and disk corruption
- Certificate expiration and PKI failures
- DNS poisoning and service discovery attacks

**Application Threats:**
- Supply chain attacks via compromised dependencies
- Secrets exposed in container images or logs
- Injection attacks through application vulnerabilities
- Business logic flaws in microservices
- API security vulnerabilities and rate limiting bypasses

**Trust Threats:**
- Compromised container registries and image repositories
- Man-in-the-middle attacks on cluster communications
- Admission controller bypasses and policy violations
- Service mesh certificate authority compromise
- Third-party operator and plugin vulnerabilities
