#### Parser Content
```Java
{
Name = cisco-acs-auth-success
  DataType = "authentication-successful"
  Conditions = [ """|Cisco Secure ACS|""", """categoryOutcome=/Success""","""destinationServiceName=Login""" ]
}
${CiscoParsersTemplates.cef-acs-auth} {
  Name = cisco-acs-auth-success-2
  DataType = "authentication-successful"
  Conditions = [ """|Cisco Secure ACS|""", """|Authentication succeeded|""" ]
}
${CiscoParsersTemplates.cef-acs-auth} {
  Name = cisco-acs-auth-failed
  DataType = "authentication-failed"
  Conditions = [ """|Cisco Secure ACS|""", """|Authentication failed|""" ]
}
${CiscoParsersTemplates.cef-acs-auth} {
  Name = cisco-acs-system-activity-1
  DataType = "app-activity"
  Conditions = [ """|Cisco Secure ACS|""", """categoryOutcome=/Success""" ]
}
{
  Name = cisco-ftd-permit-any
  Vendor = Cisco
  Product = Cisco Firepower
  Lms = Syslog
  DataType = "network-connection"
  TimeFormat = "yyyy-MM-dd HH:mm:ss"
  Conditions = [ """%FTD-""", """Permit Any""" ]
  Fields = [
    """exabeam_time=({time}\d\d\d\d-\d\d-\d\d \d\d:\d\d:\d\d)""",
    """({host}[\w\-.]+)\s*%FTD-""",
    """%FTD-({priority}\d+)-({event_code}\d+)\\?""",
    """({event_name}Permit Any)""",
    """AccessControlRuleAction="+({outcome}[^"]+)"+""",
    """SrcIP="+({src_ip}[^"]+)"+""",
    """DstIP="+({dest_ip}[^"]+)"+""",
    """SrcPort="+({src_port}[^"]+)"+""",
    """DstPort="+({dest_port}[^"]+)"+""",
    """\sProtocol="+({protocol}[^"]+)"+""",
    """IngressInterface="+({ingress_interface}[^"]+)"+""",
    """EgressInterface="+({egress_interface}[^"]+)"+""",
    """DeviceUUID="+({device_id}[^"]+)"+""",
    """Client="+({app}[^"]+)"+""",
    """ApplicationProtocol="+({app_protocol}[^"]+)"+""",
    """InitiatorBytes="+({bytes_in}[^"]+)"+""",
    """ResponderBytes="+({bytes_out}[^"]+)"+""",
    """NAPPolicy="+({nap_policy}[^"]+)"+""",
    """URL="+({full_url}[^"]+)"+""",
    """InitiatorPackets="+({initiator_packets}[^"]+)"+""",
    """ResponderPackets="+({responder_packets}[^"]+)"+""",
    """User="+(No Authentication Required|({user}[^"]+))"+""",
  ]
  DupFields = [ "outcome->action" ]
}
```