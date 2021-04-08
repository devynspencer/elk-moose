# elk-moose
Quickly analyze flat files.

```powershell
# Create Windows index template
Invoke-RestMethod "http://localhost:9200/_index_template/windows" -InFile "./elasticsearch/templates/windows.json" -Method Put -ContentType application/json
```
