#### Parser Content
```Java
{
Name = cef-cyberark-security-alert-1
   Vendor = CyberArk
   Product = Privileged Threat Analytics
   Lms = Splunk
   DataType = "alert"
   TimeFormat = "epoch"
   Conditions = [ """CyberArk|PTA""" , """suser=""" ]
   Fields = [
      """deviceCustomDate1=({time}[^\s]+)"""
      """\s({host}[^\s]+)\sCEF"""
      """shost=((None)|({src_host}[^\s]+))""",
      """src=((None)|({src_ip}[^\s]+))""",
      """dst=((None)|({dest_ip}[^\s]+))""",
      """suser=((None)|({user}[^\s\(]+))""",
      """dhost=((None)|({dest_host}[^\s]+))""",
      """duser=((None)|({additional_info}[^\s\(]+))""",
      """cs2=({alert_id}[^\s]+)""",
      """CEF.+?\|.+?\|({alert_type}[^\|]+)""",
      """CEF.+?\|.+?\|.+?\|.+?\|.+?\|({alert_name}[^\|]+)\|({alert_severity}[^\|]+)"""
   ]
}
${CyberArkParserTemplates.cyberark-events-1}{
  Name = s-cyberark-failed-logon-1
  DataType = "failed-logon"
  Conditions = [ """|Window Title|""","""Command=FAILED TO INITIATE WINDOWS SESSION AUDIT""" ]
  Fields = ${CyberArkParserTemplates.cyberark-events-1.Fields} [
    """({time}\d+-\d+-\d+T\d+:\d+:\d+Z)\s+({host}[^\s]+)\s+\|({user}[^\|]+)"""
    ]
 }
```