#### Parser Content
```Java
{
Name = gravityzone-security-alert-new-login
  Product = Gravityzone
  Vendor = Gravityzone
  Lms = Direct
  DataType = "app-login"
  TimeFormat = "yyyy-MM-dd'T'HH:mm:ss"
  Conditions = [ """gravityzone:""", """"name":"Login from new device"""" ]
  Fields = [
    """exabeam_host=([^=]+@\s*)?({host}\S+)""",
    """"created":"({time}\d\d\d\d-\d\d-\d\dT\d\d:\d\d:\d\d)""",
    """({app}gravityzone)""",
    """"name":"({activity}[^"]+)""",
    """"user_name":"(({user_email}({user}[^"@\\\/\s]+)@({domain}[^.]+)[^"]+))""",
    """"os":"({os}[^"]+)""",
    """"browser_name":"({browser}[^"]+)""",
    """"device_ip":"({src_ip}[A-Fa-f:\d.]+)""",
  ]
}
```