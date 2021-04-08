# elk-moose
Quickly analyze flat files.

```powershell
# Create Windows index template
Invoke-RestMethod "http://localhost:9200/_index_template/windows" -InFile "./elasticsearch/templates/windows.json" -Method Put -ContentType application/json

# Generate event logs
$Events = Get-WinEvent -ComputerName VPN01 -FilterHashtable @{ LogName = "System"; ProviderName = "RemoteAccess"; StartTime = (Get-Date).AddDays(-5) } | ConvertTo-Json -Depth 3

# Send event logs to Logstash via HTTP listener
Invoke-RestMethod "http://localhost:8080" -Method Post -ContentType application/json -Body $Events
```
