#### Parser Content
```Java
{
Name = centrify-ssh-login
  Vendor = Centrify
  Product = Centrify
  Lms = Direct
  DataType = "remote-logon"
  TimeFormat = "epoch"
  Conditions = ["""Centrify Suite|Centrify""" , """SSHD granted"""]
  Fields = [
    """utc=({time}\d+)""",
    """exabeam_host=({host}[\w.\-]+)""",
    """\sahost=({host}[^=]+?)\s+\w+=""",
    """\sclient=(({src_ip}\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3})|({src_host}[^=]+?))\s+\w+=""",
    """user=({user}[^\(\)\s\$]+)"""
    """\d+\|\d+\|({event_name}.+?)\|\d""",
    """status=({outcome}.+?)\s\w+=""",
    """pid=({process_id}\d+)""",
    """service=({process}.+?)\s\w+=""",
    """EntityName=(.+\\+)?({dest_host}[^"\s]+)(\s|$)"""
  ]
}
{
  Name = centrify-ssh-login-failed
  Vendor = Centrify
  Product = Centrify
  Lms = Direct
  DataType = "authentication-failed"
  TimeFormat = "epoch"
  Conditions = ["""Centrify Suite|Centrify""" , """SSHD denied"""]
  Fields = [
    """utc=({time}\d+)""",
    """exabeam_host=({host}[\w.\-]+)""",
    """\sahost=({host}[^=]+?)\s+\w+=""",
    """\sclient=(({src_ip}\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3})|({src_host}[^=]+?))\s+\w+=""",
    """user=({user}[^\(\)\s\$]+)"""
    """\d+\|\d+\|({event_name}.+?)\|\d""",
    """status=({outcome}.+?)\s\w+=""",
    """pid=({process_id}\d+)""",
    """service=({process}.+?)\s\w+=""",
    """EntityName=(.+\\+)?({dest_host}[^"\s]+)(\s|$)"""
    """reason=({failure_reason}[^=\|]+?)(\s+\w+=|\|)"""
  ]
}

{
  Name = centrify-local-logon
  Vendor = Centrify
  Product = Centrify
  Lms = Direct
  DataType = "local-logon"
  TimeFormat = "epoch"
  Conditions = ["""|Centrify Suite|Trusted Path|""" , """|Trusted path granted|"""]
  Fields = [
    """exabeam_host=([^=]+@\s*)?({host}\S+)""",
    """utc=({time}\d+)""",
    """user=({user}[^\(\)\s@]+)\(""",
    """user=({user}[^\(\)\s@]+)@({domain}[^\(\)\s@]+)\s+(\w+=|$)""",
    """\|({event_name}Trusted path\s+[^\|]*)\|""",
    """status=({outcome}.+?)\s+(\w+=|$)""",
    """pid=({pid}\d+)""",
    """server=(({protocol}[^\\\/\s]+)[\\\/]+)?({dest_host}[^\\\/\s]+?)\s+(\w+=|$)""",
  ]
}
```