# AZ-104 Reviewer
# Domain: Monitor and Maintain Azure Resources

---

# 📚 Exam Coverage

This domain covers:
- Azure Monitor
- Log Analytics Workspace
- Alerts and Action Groups
- Application Insights
- Network Watcher
- Azure Backup
- Recovery Services Vault
- Azure Site Recovery (ASR)
- Monitoring Metrics and Logs
- Diagnostic Settings
- Service Health
- Advisor Recommendations

Weight in Exam:
10–15%

---

# 📊 Azure Monitor Overview

Azure Monitor is the central monitoring platform for Azure resources.

Functions:
- Collect metrics
- Collect logs
- Create alerts
- Analyze performance
- Troubleshoot issues

---

# 🔹 Azure Monitor Data Types

| Data Type | Description |
|---|---|
| Metrics | Numeric performance data |
| Logs | Detailed event records |

---

# 🔹 Metrics vs Logs

| Metrics | Logs |
|---|---|
| Lightweight | Detailed |
| Near real-time | Query-based |
| Short retention | Long-term analysis |

---

# 🔹 Azure Monitor Components

| Component | Purpose |
|---|---|
| Metrics | Performance monitoring |
| Logs | Event analysis |
| Alerts | Notifications |
| Dashboards | Visualization |
| Insights | Resource monitoring |

---

# 📈 Azure Metrics

Metrics are numerical measurements collected over time.

Examples:
- CPU percentage
- Disk usage
- Memory usage
- Network traffic

---

# 🔹 Metric Characteristics

| Characteristic | Description |
|---|---|
| Lightweight | Fast collection |
| Time-series | Trend analysis |
| Near real-time | Quick updates |

---

# 🔹 Common Metrics

| Resource | Metric Example |
|---|---|
| VM | CPU percentage |
| Storage | Transactions |
| Network | Throughput |
| App Service | Requests |

---

# 📜 Azure Logs

Logs store detailed records.

Examples:
- Security events
- Resource operations
- Application logs

---

# 🔹 Log Categories

| Log Type | Description |
|---|---|
| Activity Log | Subscription events |
| Resource Logs | Resource-specific |
| Guest OS Logs | VM operating system logs |

---

# 🔹 Activity Log

Tracks:
- Administrative operations
- Policy changes
- Resource creation/deletion

Retention:
```text
90 days by default
```

---

# 🔹 Resource Logs

Provides resource-level diagnostics.

Examples:
- NSG flow logs
- Key Vault logs
- Storage logs

---

# 🔹 Diagnostic Settings

Used to send logs and metrics to:
- Log Analytics Workspace
- Storage Account
- Event Hub

---

# 📦 Log Analytics Workspace

Central repository for log data.

Used with:
- Azure Monitor
- Sentinel
- Defender

---

# 🔹 Kusto Query Language (KQL)

Used to query logs.

---

# 🔹 KQL Example

```kusto
Heartbeat
| summarize count() by Computer
```

---

# 🔹 Common KQL Operators

| Operator | Purpose |
|---|---|
| where | Filter |
| summarize | Aggregate |
| project | Select columns |
| order by | Sort |

---

# 🚨 Azure Alerts

Automatically notify when conditions occur.

---

# 🔹 Alert Types

| Alert Type | Description |
|---|---|
| Metric Alert | Based on metrics |
| Log Alert | Based on KQL query |
| Activity Log Alert | Subscription events |

---

# 🔹 Alert Components

| Component | Purpose |
|---|---|
| Scope | Target resource |
| Condition | Trigger criteria |
| Action Group | Notification |
| Severity | Alert importance |

---

# 🔹 Alert Severity Levels

| Severity | Description |
|---|---|
| Sev 0 | Critical |
| Sev 1 | Error |
| Sev 2 | Warning |
| Sev 3 | Informational |
| Sev 4 | Verbose |

---

# 🔹 Action Groups

Defines notification actions.

---

# 🔹 Action Types

| Action | Description |
|---|---|
| Email | Send notification |
| SMS | Text alert |
| Push Notification | Mobile alert |
| Webhook | Trigger automation |
| Logic App | Automated workflow |

---

# 🔹 Alert Example

Requirement:
```text
Notify admin if CPU exceeds 80%
```

Solution:
```text
Metric Alert + Action Group
```

---

# 🖥️ VM Monitoring

Azure Monitor can monitor:
- CPU
- Memory
- Disk
- Networking

---

# 🔹 Azure Monitor Agent (AMA)

Collects telemetry from VMs.

Replaces:
- Log Analytics Agent

---

# 🔹 VM Insights

Provides:
- Performance monitoring
- Dependency mapping

---

# 🔹 Boot Diagnostics

Captures:
- VM screenshots
- Serial console logs

Useful for troubleshooting startup failures.

---

# 🌐 Network Watcher

Network diagnostic service.

---

# 🔹 Network Watcher Features

| Tool | Purpose |
|---|---|
| IP Flow Verify | Check NSG rules |
| Packet Capture | Traffic capture |
| Connection Troubleshoot | Connectivity testing |
| NSG Flow Logs | Traffic analysis |

---

# 🔹 NSG Flow Logs

Captures NSG traffic information.

Used for:
- Security analysis
- Troubleshooting

---

# 🔹 Connection Monitor

Monitors connectivity between endpoints.

---

# 📱 Application Insights

Application performance monitoring service.

Used for:
- Web applications
- APIs
- Performance analysis

---

# 🔹 Application Insights Features

| Feature | Description |
|---|---|
| Request Tracking | Monitor requests |
| Dependency Tracking | External calls |
| Exception Tracking | Error analysis |
| Availability Tests | Uptime monitoring |

---

# 🔹 Smart Detection

Automatically identifies:
- Performance anomalies
- Failures
- Dependency issues

---

# 💾 Azure Backup

Managed backup service.

---

# 🔹 Azure Backup Supports

| Resource | Supported |
|---|---|
| Azure VMs | ✅ |
| Azure Files | ✅ |
| SQL Server | ✅ |

---

# 🔹 Recovery Services Vault

Stores:
- Backups
- Replication metadata

---

# 🔹 Backup Concepts

| Concept | Description |
|---|---|
| Recovery Point | Backup snapshot |
| Retention Policy | Backup duration |
| Restore Operation | Recover data |

---

# 🔹 Soft Delete for Backup

Prevents accidental backup deletion.

Retention:
```text
14 days by default
```

---

# 🔹 Backup Types

| Backup Type | Description |
|---|---|
| Full | Complete copy |
| Incremental | Changed data only |

---

# 🔄 Azure Site Recovery (ASR)

Disaster recovery service.

---

# 🔹 ASR Features

| Feature | Description |
|---|---|
| Replication | Copy workloads |
| Failover | Switch to DR site |
| Failback | Return to primary |

---

# 🔹 ASR Use Cases

- Datacenter disaster recovery
- Business continuity
- Migration

---

# 🔹 Planned vs Unplanned Failover

| Type | Description |
|---|---|
| Planned | Controlled failover |
| Unplanned | Emergency failover |

---

# 🌍 Azure Service Health

Provides Azure platform health information.

---

# 🔹 Service Health Types

| Type | Description |
|---|---|
| Service Issues | Azure outages |
| Planned Maintenance | Upcoming maintenance |
| Health Advisories | Recommendations |

---

# 🔹 Resource Health

Provides health status of individual resources.

Statuses:
- Available
- Unavailable
- Degraded

---

# 💡 Azure Advisor

Provides optimization recommendations.

---

# 🔹 Advisor Categories

| Category | Purpose |
|---|---|
| Cost | Reduce expenses |
| Security | Improve security |
| Reliability | Increase uptime |
| Performance | Improve efficiency |

---

# 🔥 Important Exam Concepts

---

# 🔹 Metrics vs Logs

| Metrics | Logs |
|---|---|
| Numerical | Detailed records |
| Near real-time | Query-based |

---

# 🔹 Alert Selection

| Requirement | Alert Type |
|---|---|
| CPU threshold | Metric Alert |
| Resource deletion | Activity Log Alert |
| Query-based monitoring | Log Alert |

---

# 🔹 Monitoring Storage Options

| Destination | Purpose |
|---|---|
| Log Analytics | Query analysis |
| Storage Account | Long retention |
| Event Hub | SIEM integration |

---

# ⚠️ Common Exam Confusions

---

# Azure Monitor vs Log Analytics

| Azure Monitor | Log Analytics |
|---|---|
| Monitoring platform | Log data repository |

---

# Activity Log vs Resource Logs

| Activity Log | Resource Logs |
|---|---|
| Subscription-level | Resource-level |

---

# Backup vs Site Recovery

| Backup | Site Recovery |
|---|---|
| Data protection | Disaster recovery |

---

# Planned vs Unplanned Failover

| Planned | Unplanned |
|---|---|
| Controlled | Emergency |

---

# 🧪 Common Exam Scenarios

---

# Scenario 1

Requirement:
```text
Notify administrators when VM CPU exceeds 90%.
```

Answer:
```text
Metric Alert
```

---

# Scenario 2

Requirement:
```text
Query VM logs using KQL.
```

Answer:
```text
Log Analytics Workspace
```

---

# Scenario 3

Requirement:
```text
Monitor Azure platform outages.
```

Answer:
```text
Azure Service Health
```

---

# Scenario 4

Requirement:
```text
Protect VM against regional disaster.
```

Answer:
```text
Azure Site Recovery (ASR)
```

---

# Scenario 5

Requirement:
```text
Capture VM startup troubleshooting information.
```

Answer:
```text
Boot Diagnostics
```

---

# Scenario 6

Requirement:
```text
Store diagnostic logs for long-term retention.
```

Answer:
```text
Storage Account
```

---

# Scenario 7

Requirement:
```text
Analyze blocked NSG traffic.
```

Answer:
```text
NSG Flow Logs
```

---

# 🧠 Memorization Tips

---

# Remember:

## Azure Monitor
Main monitoring platform

## Log Analytics
Log storage and queries

## KQL
Query language

## Metric Alert
Threshold monitoring

## Activity Log
Subscription events

## Resource Logs
Resource diagnostics

## Backup
Data protection

## Site Recovery
Disaster recovery

## Service Health
Azure platform status

---

# 🛠️ Recommended Hands-On Practice

Practice:
- Create metric alerts
- Configure action groups
- Query logs using KQL
- Configure diagnostic settings
- Enable VM Insights
- Enable boot diagnostics
- Configure Azure Backup
- Configure Site Recovery
- Use Network Watcher tools
- Review Service Health alerts

---

# 📖 Official Microsoft Resources

AZ-104 Skills Measured:
https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/az-104/

Azure Monitor Documentation:
https://learn.microsoft.com/en-us/azure/azure-monitor/

Log Analytics Documentation:
https://learn.microsoft.com/en-us/azure/azure-monitor/logs/

Azure Backup Documentation:
https://learn.microsoft.com/en-us/azure/backup/

Azure Site Recovery Documentation:
https://learn.microsoft.com/en-us/azure/site-recovery/

Application Insights Documentation:
https://learn.microsoft.com/en-us/azure/azure-monitor/app/app-insights-overview/
