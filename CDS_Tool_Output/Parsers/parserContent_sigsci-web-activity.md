#### Parser Content
```Java
{
Name = sigsci-web-activity
  Vendor = SIGSCI 
  Product = SIGSCI
  Lms = Direct 
  DataType = "web-activity"
  TimeFormat ="yyyy-MM-dd'T'HH:ss:SSZ"
  Conditions = [ """serverHostname""", """remoteHostname""", """serverName""", """uri"""]
  Fields = [
    """"+serverHostname"+:"+({src_host}[^"]+)""",
    """"+remoteIP"+:"+({dest_ip}[^"]+)""",
    """"+remoteHostname"+:"+({dest_host}[^"]+),""",
    """"+userAgent"+:"+({user_agent}[^"]+)""",
    """"+timestamp"+:"+({time}[^"]+)""",
    """"+method"+:"+({method}[^"]+)""",
    """"+path"+:"+({uri_path}[^"]+)""",
    """"+responseCode"+:({result_code}\d+)""",
    """"+Host"+."+({host}[^"]+)""",
    """BLOCKED"+":\s*\{"+type"+:"+({action}[^"]+)""",
    """"+protocol"+:"+({protocol}[^"]+)""",
    """"+Content-Type"+:"+({mime}[^";]+)""",
    """"+responseSize"+:({bytes_out}\d+)"""
    ]
}

{
    Name = ifilter-web-activity
    Vendor = Digital Arts
    Product = Digital Arts i-FILTER for Business
    Lms = Direct
    DataType = "web-activity"
    IsHVF = true
    TimeFormat = "dd/MMM/yyyy:HH:mm:ss Z"
    Conditions = [ """[proxyIfilter:""" ]
    Fields = [
      """exabeam_host=([^=]+@\s*)?({host}\S+)""",
      """\w+ \d+ \d\d:\d\d:\d\d \d+ \S+ (-|({dest_ip}[A-Fa-f:\d.]+)) (-|({src_ip}[A-Fa-f:\d.]+)) (-|({src_host}\S+)) (-|({user}[^\s]+)) \[({time}\d+\/\w+\/\d\d\d\d:\d\d:\d\d:\d\d [+-]\d+)\] ({result_code}\d+) ({bytes_out}\d+) ({bytes_in}\d+) ({action}\S+) \S+ ({reason}\S+) ({category}\S+).+?"({method}\S+) ({full_url}(({protocol}\w+):[\\\/]+)?({web_domain}[^\\\/\s:]+)({uri_path}\/[^\s\?]+)?({uri_query}\?[^\s"]+)?)[^"]*" (-|({referrer}\S+)) (-|({user_agent}.+?)) \S+ \S+\s*$""",
      """({top_domain}[^\\\/\s."]+(?:\.(?:com|net|info|edu|org|gov|co|jp|ru|de|ir|it|in|fr|info|pl|nl|es|gr|cz|eu|tv|me|jp|ca|cn|uk|my|cc|id|us|nz|biz|club|io|gg|fi|au|st|tw|asia|sg|ie|li|za))+)(:|\/|\s)""",
      """(Mozilla.+({os}iOS|Android|BlackBerry|Windows Phone|BeOS|(?:X|x)11|(?:W|w)indows|(?:L|l)inux|(?:M|m)acintosh|(?:D|d)arwin).+?({browser}Chrome|Safari|Opera|(?:F|f)irefox|MSIE|Trident))""",
    ]
  }
```