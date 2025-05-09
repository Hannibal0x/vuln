# EdenSoft Office Intelligent Assistant 3.0.0.0 has XSS


## Vulnerability Type :
XSS


## Vulnerability Version :
3.0.0.0

## Vulnerability Description AND recurrence:
The EdenSoft Office Intelligent Assistant is an internal enterprise office support platform built on Azure OpenAI services, offering AI-powered office capabilities including intelligent Q&A and image creation.
During interactions with the AI application, both user inputs and system outputs lack filtering. XSS attack payloads are persistently stored in session histories.

Input-Side Trigger
Users can craft malicious inputs. The AI application fails to filter or escape these inputs, allowing the execution of external JavaScript scripts. This may lead to XSS exploitation and risks of sensitive data leakage.
Example:
`<img src=x onerror="console.log('XSS')">`
![Input-Side Trigger](./1.png)

Output-Side Trigger
Attackers may exploit inherent flaws in the AI application to induce the model to autonomously generate malicious payloads in outputs. Without proper filtering or escaping, these payloads could execute external JavaScript scripts, triggering XSS and potential data breaches.
Note: Output-side exploitation depends on the model’s behavior, possesses a certain degree of randomness, and cannot guarantee 100% success in fulfilling attackers’ intentions.
Example:
`xss img onerror trigger alert(1)`
![Output-Side Trigger](./2.png)

This vulnerability was validated in the vendor’s internal test environment. Risk assessments and remediation recommendations have been communicated to Shenzhen Eden Software Co., Ltd.
