#### Parser Content
```Java
{
Name = s-azure-ad-app-login-2
  Vendor = Microsoft
  Product = Microsoft Azure Active Directory
  Lms = Splunk
  DataType = "app-login"
  TimeFormat = "yyyy-MM-dd'T'HH:mm:ss.SSSSSSSZ"
  Conditions = [ """authenticationMethod""", """riskLevelDuringSignIn""", """ms:aad:signin""","""tokenIssuerType""" ]
  Fields = [
    """exabeam_host=([^=]+@\s*)?({host}\S+)""",
    """"createdDateTime"+:\s*"+({time}[^"]+)""",
    """ms:aad:signin"+,"+({host}[^"]+)""",
    """"userPrincipalName"+:\s*"+({user_email}[^"\s@]+@[^"\s@]+)""",
    """"ipAddress"+:\s*"+({src_ip}[A-Fa-f:\d.]+)""",
    """"browser"+:\s*"+({browser}[^"]+)""",
    """"operatingSystem"+:\s*"+({os}[^"]+)""",
    """"userDisplayName"+:\s*"+({user_fullname}[^"]+)""",
    """"failureReason"+:\s*"+(Other|({failure_reason}[^"]+))""",
    """"errorCode"+:\s*({error_code}\d+)""",
    """"appDisplayName"+:\s*"+({app}[^"]+)""",
    """"location"+:\s*\{"+({additional_info}.+?)\}
```