#### Parser Content
```Java
{
Name = json-microsoft-app-activity-6
  Product = Office 365
  Conditions= [ """"activityType":"Group"""", """"activityOperationType":"Update"""", """"targetResourceType":"""" ]
}
${MSParserTemplates.json-microsoft-app-activity} {
  Name = json-microsoft-app-activity-8
  Product = Office 365
  Conditions= [ """"activityType":"Group"""", """"activityOperationType":"Assign"""", """"targetResourceType":"""" ]
}
${MSParserTemplates.json-microsoft-app-activity} {
  Name = json-microsoft-app-activity-9
  Product = Office 365
  Conditions= [ """"activityType":"User"""", """"activityOperationType":"Add"""", """"targetResourceType":"""" ]
}
${MSParserTemplates.json-microsoft-app-activity} {
  Name = json-microsoft-app-activity-10
  Product = Office 365
  Conditions= [ """"activityType":"User"""", """"activityOperationType":"Delete"""", """"targetResourceType":"""" ]
}
${MSParserTemplates.json-microsoft-app-activity} {
  Name = json-microsoft-app-activity-11
  Product = Office 365
  Conditions= [ """"activityType":"User"""", """"activityOperationType":"Restore"""", """"targetResourceType":"""" ]
}
${MSParserTemplates.json-microsoft-app-activity} {
  Name = json-microsoft-app-activity-12
  Product = Office 365
  Conditions= [ """"activityType":"User"""", """"activityOperationType":"Update"""", """"targetResourceType":"""" ]
}
${MSParserTemplates.json-microsoft-app-activity} {
  Name = json-o365-file-write-7
  Product = Office 365
  Conditions= [ """"Operation":"FileUploaded"""", """"Workload":"""", """"SourceFileName":"""" ]
}
```