#### Parser Content
```Java
{
Name = cef-duo-failed-app-login-1
  Vendor = Duo Security
  Product = Duo Security
  Lms = ArcSight
  DataType = "app-login"
  TimeFormat = "epoch"
  Conditions = [ """CEF:""", """|Duo Security|Two-Factor|""", """|FAILURE|""" ]
  Fields = [
    """\|Duo Security\|({login_type}[^\|]+)\|[^\|]*\|({outcome}[^\|]+)\|""",
    """\scat=({failure_reason}.+?)\s+(\w+=|$)""",
    """\srt=({time}\d+)""",
    """\ssrc=({src_ip}[a-fA-F\d.:]+)""",
    """\ssuser=({user}.+?)\s+(\w+=|$)""",
    """\ssproc=({app}.+?)\s+(\w+=|$)""",
    """\sdvc=({host}.+?)\s+(\w+=|$)""",
    """\sdvchost=({host}.+?)\s+(\w+=|$)""",
  ]
}
```