#### Parser Content
```Java
{
Name = cef-mcafee-usb
    Vendor = McAfee
    Product = McAfee DLP
    Lms = ArcSight
    DataType = "dlp-alert"
    TimeFormat = "epoch"
    Conditions = [ """CEF:""", """|McAfee|ePolicy""", """|Threat:""" ]
    Fields = [ """\srt=({time}\d+)""",
      """\sdvchost=({host}[^\s]+)""",
      """\sexternalId=({alert_id}\d+)""",
      """CEF([^\|]*\|){5}({alert_name}[^|]+)""",
      """CEF([^\|]*\|){6}({alert_severity}[^|]+)""",
      """\smsg=({alert_type}.+?)\s+\w+=""",
      """\smsg=({activity_details}.+?)\s+\w+=""",
      """\smsg=.+?(MONITOR|, PERMITTED)\s+({device_type}.+?)\s+\w+=""",
      """\sshost=({dest_host}[^\s]+)""",
      """\ssrc=({dest_ip}\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3})""",
      """\ssuser=(({domain}[^\\]+)\\+)?({user}.+?)\s+\w+="""
    ]
  }
```