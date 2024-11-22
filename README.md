# learn-aws-guardduty
How to use and remediate guard duty

- [ ] https://aws.github.io/aws-security-services-best-practices/guides/guardduty/
- [ ] https://d1.awsstatic.com/events/Summits/reinvent2022/SEC301-R_Threat-detection-and-response-workshop.pdf
- [ ] https://mng.workshop.aws/operations/detect/guardduty.html

### How to loop until findings appear
```bash
while [[ -n $(aws guardduty list-findings --detector-id $(aws guardduty list-detectors --query DetectorIds[*] --output text)) ]]; do echo "$(aws guardduty list-findings --detector-id $(aws guardduty list-detectors --query DetectorIds[*] --output text))"; sleep 10; done; echo "Findings detected"
```

### GuardDuty Sample Findings Checklist

#### EC2 Findings
- [ ] EC2PortScan
- [ ] EC2SshBruteForce
- [ ] EC2RDPBruteForce
- [ ] EC2MaliciousIPCaller
- [ ] EC2OutboundConnectionToTor
- [ ] EC2CryptoCurrencyActivity
- [ ] EC2DNSDataExfiltration
- [ ] EC2PublicIPMisconfiguration
- [ ] EC2Behavior:UnusualTrafficVolume

#### IAM Findings
- [ ] IAMUnauthorizedAccess
- [ ] IAMAnomalousBehavior:UnusualLocation
- [ ] IAMAnomalousBehavior:AnomalousCredentialUsage
- [ ] IAMPolicyMisconfiguration
- [ ] IAMAccessKeyCompromised
- [ ] IAMExcessivePermissions

#### S3 Findings
- [ ] S3BlockPublicAccessDisabled
- [ ] S3PublicAccessEnabled
- [ ] S3DataExfiltration
- [ ] S3AnomalousBehavior:LargeDataDownload
- [ ] S3AnomalousBehavior:LargeDataUpload
- [ ] S3RansomwareActivity

#### RDS Findings
- [ ] RDSUnusualBehavior:DataExfiltration
- [ ] RDSInstanceCompromised

#### EKS Findings
- [ ] EKSClusterMisconfiguration
- [ ] EKSUnusualContainerActivity
- [ ] EKSNetworkIntrusionDetected

#### Lambda Findings
- [ ] LambdaUnauthorizedAccess
- [ ] LambdaInvocationFromMaliciousIP
- [ ] LambdaAnomalousBehavior:FunctionModification
- [ ] LambdaMisconfiguration

#### General Findings
- [ ] UnauthorizedAccessFromMaliciousIP
- [ ] UnusualIPAccessToAWSAccount
- [ ] APIKeyMisuse
- [ ] ConfigurationChangeWithoutAuthorization

#### Reconnaissance Findings
- [ ] UnusualAPIRequests:Reconnaissance
- [ ] UnusualIPActivity:Reconnaissance
- [ ] AccountReconnaissanceFromNewRegion

#### Unusual Behavior Findings
- [ ] UnusualAPICalls
- [ ] UnusualTrafficPatterns
- [ ] LoginFromNewLocation
- [ ] CredentialUsageWithUnusualPattern
- [ ] CompromisedResourceDetected

#### VPC Findings
- [ ] VPCNetworkTrafficAnomaly
- [ ] VPCUnusualOutboundTraffic
- [ ] VPCPolicyViolation


## How to trigger guardduty
Using nimbostratus

https://github.com/andresriancho/nimbostratus

https://andresriancho.github.io/nimbostratus/

Explain

https://rhinosecuritylabs.com/cloud-security/aws-security-vulnerabilities-perspective/
