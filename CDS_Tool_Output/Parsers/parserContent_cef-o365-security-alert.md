#### Parser Content
```Java
{
Name = cef-o365-security-alert
  Vendor = Microsoft
  Product = Office 365
  Lms = ArcSight
  DataType = "alert"
  TimeFormat = "yyyy-MM-dd'T'HH:mm:ss"
  Conditions = [ """CEF:""", """|Skyformation|SkyFormation Cloud Apps Security|""", """|security-threat-detected|""", """cat=security-alert""", """=Office 365"""]
  Fields = [
    """({time}\d\d\d\d-\d\d-\d\dT\d\d:\d\d:\d\d)\.\d+Z\s+({host}[\w\-.]+)\s+Skyformation"""
    """({alert_type}({alert_name}IdentityProtection))"""
    """({alert_type}({alert_name}graph-identity-protection-risk-detection))"""
    """"source":"(generic|({alert_type}[^"]+))"""",
    """"riskType":"(generic|({alert_name}[^"]+))"""",
    """"requestId":"({alert_id}[^"]+)"""",
    """"riskLevel":"({alert_severity}[^"]+)"""",
    """"riskType":"({threat_category}[^"]+)"""",
    """"ipAddress":"({src_ip}[A-Fa-f:\d.]+)"""",
    """"userDisplayName":"({user_fullname}[^"]+)"""",
    """"userPrincipalName":"({user_email}[^"@\s]+@[^"@\s]+)"""",
    """msg=({additional_info}.+?)\s+(\w+=|$)""",
    """activity":"({activity}[^"]+)""",
    """"+userAgent"+,"+Value"+:"+({user_agent}[^"]+)""",
    """destinationServiceName=({app}.*?)\s*deviceInboundInterface"""
    """"detectedDateTime"+:"+({time}\d+-\d+-\d+T\d+:\d+:\d+)""",
    """"tokenIssuerType"+:"+({token_issuer_type}[^"]+)""",
    """"+activity"+:"+({action}[^"]+)""",
    """"+additionalInfo"+:"+\[\{\\"+({more_info}[^]]+)\\"*"""
    """flexString1=({activity}.+?)\s*\w+=""",
    """"Name"+:"+({alert_name}[^"]+)""",
    """request=({outcome}.+?)\s*\w+=""",
    """"Severity"+:"+({alert_severity}[^"]+)""",
    """"sev"+:"+({alert_severity}[^"]+)""",
    """"riskLevel"+:"+({alert_severity}[^"]+)""",
    """"AlertType"+:"+({alert_type}[^"]+)""",
    """"tsd\\*"+:\\*"+({sender}[^\\"]+)""",
    """"sip\\*"+:\\*"+({src_ip}[^\\"]+)""",
    """"ms\\*"+:\\*"+({subject}.+?)\s*"+""",
    """"city"+:"+({location_city}[^"]+)""",
    """"countryOrRegion"+:"+({country_code}[^"]+)""",
    """"state"+:"+({location_state}[^"]+)"""
  ]
}
```