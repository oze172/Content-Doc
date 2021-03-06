#### Parser Content
```Java
{
Name = s-mdam-db-query
  Vendor = McAfee
  Product = MDAM
  Lms = Splunk
  DataType = "database-query"
  IsHVF = true
  TimeFormat = "dd MMM yyyy HH:mm:ss"
  Conditions = [ """db_user=""", """db_type=""" ]
  Fields = [
    """\d\d:\d\d:\d\d\s+({host}[^\s]+)\s+(\w+=|$)""",
    """execution_time="({time}\d\d \w{3} \d{4} \d\d:\d\d:\d\d)""",
    """src_ip="({src_ip}\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3})""",
    """os_user="(NULL|(({domain}[^\\"]+)\\+)?({os_user}.+?)\s*)"""",
    """cmdtype="({db_operation}[^"]+)"""",
    """sqlstmt="({db_query}.+?)\s*"+\s*(\w+=|$)""",
    """db_name="({database_name}[^"]+)"""",
    """src_host="({src_host}[^"]+)"""",
    """db_user="(NULL|(({db_domain}[^\\"]+)\\+)?({db_user}.+?)\s*)"""",
    """schema="(NULL|({schema}[^"]+))"""",
    """db_type="({app}[^"]+)"""",
    """sid="({user_sid}[^"]+)"""",
    """accessed_objects="(NULL|({additional_info}[^"]+))""""
  ]
  DupFields = [ "db_user->account", "os_user->user" ]
}

{
  Name = cef-mdam-db-alert
  Vendor = McAfee
  Product = MDAM
  Lms = ArcSight
  DataType = "database-alert"
  IsHVF = true
  TimeFormat = "epoch"
  Conditions = [ """CEF:""", """|McAfee|DAM|""", """|alert|""", """externalId=""" ]
  Fields = [
    """\Wrt=({time}\d+)""",
    """\Wcs1=MSSQL:({host}[\w\-.]+)""",
    """\WexternalId=({alert_id}\d+)""",
    """\Wdst=({dest_ip}[A-Fa-f:\d.]+)""",
    """\Wsrc=({src_ip}[A-Fa-f:\d.]+)""",
    """\Wduser=((|NT AUTHORITY|({domain}[^\\\s]+))\\+)?(|SYSTEM|({user}[^\\\s]+))\s+(\w+=|$)""",
    """\Wsuser=((|NT AUTHORITY|({domain}[^\\\s]+))\\+)?(|SYSTEM|({user}[^\\\s]+))\s+(\w+=|$)""",
    """\Wshost=({src_host}[\w\-.]+)""",
    """\Wact=({alert_type}.+?)\s+(\w+=|$)""",
    """\Wcs2=\s*({additional_info}.+?)\s+(\w+=|$)""",
    """\|alert\|({alert_name}[^\|]+)""",
  ]
}
```