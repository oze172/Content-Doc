#### Parser Content
```Java
{
Name = cef-microsoft-app-activity-11
  Product = Office 365
  Conditions= [ """CEF:""", """|Skyformation|SkyFormation Cloud Apps Security|""", """destinationServiceName=Office 365""", """|user-undeleted|""" ]
}

${MSParserTemplates.cef-microsoft-app-activity} {
  Name = cef-microsoft-app-activity-12
  Product = Office 365
  Conditions= [ """CEF:""", """|Skyformation|SkyFormation Cloud Apps Security|""", """destinationServiceName=Office 365""", """|user-updated|""" ]
}

${MSParserTemplates.cef-microsoft-app-activity} {
  Name = cef-microsoft-app-activity-13
  Product = Microsoft Azure
  Conditions= [ """CEF:""", """|Skyformation|SkyFormation Cloud Apps Security|""", """destinationServiceName=Azure""", """|resource-downloaded|""" ]
}

${MSParserTemplates.cef-microsoft-app-activity} {
  Name = cef-microsoft-app-activity-17
  Product = Office 365
  Conditions= [ """CEF:""", """|Skyformation|SkyFormation Cloud Apps Security|""", """destinationServiceName=Office 365""", """|resource-content-updated|""" ]
}

${MSParserTemplates.cef-microsoft-app-activity} {
  Name = cef-microsoft-app-activity-18
  Product = Office 365
  Conditions= [ """CEF:""", """|Skyformation|SkyFormation Cloud Apps Security|""", """destinationServiceName=Office 365""", """|resource-created|""" ]
}

${MSParserTemplates.cef-microsoft-app-activity} {
  Name = cef-microsoft-app-activity-39
  Product = Office 365
  Conditions= [ """CEF:""", """|Skyformation|SkyFormation Cloud Apps Security|""", """"Operation":"MoveToDeletedItems"""" ]
  Fields = ${MSParserTemplates.cef-microsoft-app-activity.Fields} [
    """"ParentFolder":.+?"Path":"\\*({object}[^"]+)"""",
    """"DestFolder":.+?"Path":"\\*({object}[^"]+)"""",
    """\Wfname=\s*({object}.+?)\s+(\w+=|$)""",
    """"target_object":"({object}[^"]+?)""""
    """sourceServiceName=({app}.+?)\s+(\w+=|$)""",
    """requestMethod=({app}.+?)\s+(\w+=|$)""",   
    """ext_userAgent_name=({resource}.+?)\s+(\w+=|$)""",
    """({activity}MoveToDeletedItems)""" 
  ]
}

${MSParserTemplates.cef-microsoft-app-activity} {
  Name = cef-microsoft-app-activity-19
  Product = Office 365
  Conditions= [ """CEF:""", """|Skyformation|SkyFormation Cloud Apps Security|""", """destinationServiceName=Office 365""", """|resource-deleted|""" ]
  Fields = ${MSParserTemplates.cef-microsoft-app-activity.Fields} [
    """"ParentFolder":.+?"Path":"\\*({object}[^"]+)"""",
    """"DestFolder":.+?"Path":"\\*({object}[^"]+)"""",
  ]
}

{
  Name = o365-inbox-rules
  Vendor = Microsoft
  Product = Office 365
  Lms = Direct
  DataType = "app-activity"
  TimeFormat = "yyyy-MM-dd'T'HH:mm:ss"
  Conditions = ["""Operation":"Set-Mailbox""" , """DeliverToMailboxAndForward""" ]
  Fields = [
    """"CreationTime":"({time}\d\d\d\d-\d\d-\d\dT\d\d:\d\d:\d\d)"""",
    """Forward.+?Value":"(smtp:)?({target}[^"]+@({target_domain}[^"]+))""""
    """"ResultStatus":"({outcome}[^"]+)"""",
    """"ClientIP":"({src_ip}[^:]+):""",
    """({activity}DeliverToMailboxAndForward)"""",
    """msg=({additional_info}.+?)\srequest=""",
    """"Value":"(smtp:)?.+?@({target_domain}[^"]+)"""",
    """UserId":"({user_email}[^"\\\s@]+@({user_domain}[^"\\\s@]+))""",
    """({app}Office 365)"""
    """destinationServiceName=({app}.+?)\sdevice"""
  ]
}
```