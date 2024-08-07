
## **Abstract**
- Ensuring the reliability and availability of cloud services necessitates efficient RCA for cloud incidents.
- Traditional RCA methods which relies on manual investigations of data sources such as logs, alerts and traces are often laborious, error prone and challenging.
- RCACopilot is an on-call system empowered by LLM for automating RCA of cloud incidents.
- RCACopilot matches the incoming incident handlers based on their alerts types, aggregates the critical runtime diagnostic information, predicts the incidents root cause category, and provides an explanatory narrative.
- It achieved 0.766 RCA accuracy.

Cloud computing serves as one of the most important infrastructure. With the growing adoption of Cloud Services, maintaining the **reliability**, **availability** and **security** is increasingly vital.

But, as with great power cloud systems comes with its own complexity. These complexity makes the system more vulnerable to variety of incidents that can pose a significant challenges to above three crucial properties.

### Typical Incident Life Cycle
- Detection
- Triaging
- Diagnosis
- Mitigation

**Detection:** When an anomalous system behaviour has been observed, an alert is raised by the system or users of the service.

**Triaging:** Once detected, this incident will be assigned to the appropriate engineering team.

**Diagnosis:** Assigned On-call engineer analyses different aspects of the issue and have several round of back and forth communication to identify the root cause.

**Mitigation:** Once analysed, several actions are taken by the on-call engineer to mitigate the issue and restore the service to be performing health.

