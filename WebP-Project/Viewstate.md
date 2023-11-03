## 개발환경 : visual studio 2019 webform
## 실행결과 
#### 6-1
https://github.com/gryrryfh/web-programming/assets/50912987/4580e8f2-dbda-4022-9ba7-a60cf482ed65
#### 6-2
https://github.com/gryrryfh/web-programming/assets/50912987/b8d2c5ea-3742-4f86-9df3-c08005f65cbf
#### 6-3

## 코드
### 6-1
### html
```html
<%@ Page Language="C#" AutoEventWireup="true" ViewStateEncryptionMode="Always" EnableViewStateMAC="false" CodeFile="PitchRaising.aspx.cs" Inherits="PitchRaising" %>

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">

<html xmlns="http://www.w3.org/1999/xhtml">
<head runat="server">
    <title></title>
    <style type="text/css">
        .style1
        {
            text-align: center;
        }
    </style>
</head>
<body>
    <form id="form1" runat="server">
    <div class="style1">
    
        <asp:Label ID="lblTitle" runat="server" Font-Size="Large" Text="피치를 올려라!"></asp:Label>
        <br />
        <br />
        <asp:Button ID="btnPitchDown" runat="server" onclick="btnPitchDown_Click" 
            Text="한 음 내리기" />
&nbsp;&nbsp;
        <asp:Label ID="lblPitch" runat="server" Text="라"></asp:Label>
&nbsp;&nbsp;
        <asp:Button ID="btnPitchUp" runat="server" onclick="btnPitchUp_Click" 
            Text="한 음 올리기" />
    
    </div>
    </form>
</body>
</html>
```
### aspx.cs
```c#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Web;
using System.Web.UI;
using System.Web.UI.WebControls;

public partial class PitchRaising : System.Web.UI.Page
{
    protected string[] PitchArray = { "도", "레", "미", "파", "솔", "라", "시" };
    protected int Note;

    protected void Page_Load(object sender, EventArgs e)
    {
        if (IsPostBack)
        {
            Note = (int)ViewState["Note"];
        }
        else Note = 5;
    }

    protected void Page_PreRender(object sender, EventArgs e)
    {
        ViewState["Note"] = Note;
    }

    protected void btnPitchDown_Click(object sender, EventArgs e)
    {
        Note = (int)ViewState["Note"] - 1;
        if (Note < 0) Note = 6;

        ShowPitch();
    }

    protected void btnPitchUp_Click(object sender, EventArgs e)
    {
        Note = ((int)ViewState["Note"] + 1) % 7;
        ShowPitch();
    }

    protected void ShowPitch()
    {
        lblPitch.Text = PitchArray[Note];
    }
}
```

### 6-2
```html
<%@ Page Language="C#" AutoEventWireup="true" CodeFile="FileSearch.aspx.cs" Inherits="FileSearch" %>

<!DOCTYPE html>

<html xmlns="http://www.w3.org/1999/xhtml">
<head runat="server">
<meta http-equiv="Content-Type" content="text/html; charset=utf-8"/>
    <title></title>
</head>
<body>
    <form id="form1" runat="server">
        <div style="text-align: center">
            검색어를 포함하는 파일 검색 <br />
            검색어 :
            <asp:TextBox ID="txtKeyWord" runat="server"></asp:TextBox>
            <br />
            파일형 :
            <asp:DropDownList ID="ddlFileType" runat="server">
                <asp:ListItem Value="0">워드(*.doc)</asp:ListItem>
                <asp:ListItem Value="1">파워포인트(*.ppt)</asp:ListItem>
                <asp:ListItem Value="2">한글(*.hwp)</asp:ListItem>
                <asp:ListItem Value="3">어도비(*.pdf)</asp:ListItem>
            </asp:DropDownList>
            <br />
            <asp:Button ID="btnSearch" runat="server" Text="검색어 보기"  PostBackUrl="~/FileSearchResult.aspx" />
        </div>
    </form>
</body>
</html>
```
```html
<%@ Page Language="C#" AutoEventWireup="true" CodeFile="FileSearchResult.aspx.cs" Inherits="FileSearchResult" %>

<!DOCTYPE html>

<html xmlns="http://www.w3.org/1999/xhtml">
<head runat="server">
<meta http-equiv="Content-Type" content="text/html; charset=utf-8"/>
    <title></title>
</head>
<body>
    <form id="form1" runat="server">
        <div style="text-align: center">
            검색어를 포함하는 파일 검색 <br />
            <asp:HyperLink ID="InkSearchString" Target="_blank" runat="server">HyperLink</asp:HyperLink>
&nbsp;
            <asp:Button ID="btnGoBack" PostBackUrl="~/FileSearch.aspx" runat="server" Text="이전 페이지로 가기" />
        </div>
    </form>
</body>
</html>
```
``` c#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Web;
using System.Web.UI;
using System.Web.UI.WebControls;

public partial class FileSearchResult : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        if (PreviousPage != null)
        {
            TextBox txtKeyWord;
            txtKeyWord = (TextBox)PreviousPage.FindControl("txtKeyWord");
            DropDownList ddlFileType;
            ddlFileType = (DropDownList)PreviousPage.FindControl("ddlFileType");

            string url = "http://www.google.co.kr/search?q=";
            url += Server.UrlEncode(txtKeyWord.Text + " ");

            string fileType = "";
            switch (ddlFileType.SelectedIndex)
            {
                case 0:
                    fileType = "filetype:doc";
                    break;
                case 1:
                    fileType = "filetype:ppt";
                    break;
                case 2:
                    fileType = "filetype:hwp";
                    break;
                case 3:
                    fileType = "filetype:pdf";
                    break;
            }
            url += fileType;

            InkSearchString.NavigateUrl = url;
            InkSearchString.Text = txtKeyWord.Text + " " + fileType;
        }
    }
}
```
#### 6-3
```



