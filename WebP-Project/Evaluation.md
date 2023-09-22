## 웹프로그래밍 및 데이터베이스 응용
### 3장 과제
#### 사용환경: visual studio 2019
![image](https://github.com/gryrryfh/web-programming/assets/50912987/c25b4892-2fc1-4dc7-8684-9a1cb342472f)
### 디자인
![image](https://github.com/gryrryfh/web-programming/assets/50912987/394b0796-3601-4b99-a26f-5d9fd1f58d8e)
### 코드
#### Evaluation.aspx
```c#
<%@ Page Language="C#" AutoEventWireup="true" CodeFile="Evaluation.aspx.cs" Inherits="Evaluation" %>
<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml">
<head runat="server">
<meta http-equiv="Content-Type" content="text/html; charset=utf-8"/>
    <title></title>
    <style type="text/css">
        .auto-style1 {
            width: 150px;}
        .auto-style2 {
            width: 500px; }
        .auto-style3 {
            width: 154px; }
    </style>
</head>
<body>
    <form id="form1" runat="server">
        <div>
        </div>
        <table style="border-style: solid; border-width: 1px; width: 600px; height: 210px; border-collapse: collapse; text-align: center;">
            <tr>
                <td colspan="3" style="border-style: solid; border-width: 1px">학점 계산</td>
            </tr>
            <tr>
                <td class="auto-style1" style="border-style: solid; border-width: 1px">평점</td>
                <td class="auto-style2" style="border-style: solid; border-width: 1px">
                    <asp:TextBox ID="txtScore" runat="server"></asp:TextBox>
                </td>
                <td style="border-style: solid; border-width: 1px" class="auto-style3">
                    <asp:Button ID="BtnCal" runat="server" Text="학점 계산" OnClick="BtnCal_Click1" />
                </td>
            </tr>
            <tr>
                <td class="auto-style1" style="border-style: solid; border-width: 1px">학점</td>
                <td colspan="2" style="border-style: solid; border-width: 1px">
                    <asp:Label ID="lblEvaluation" runat="server"></asp:Label>
                </td>
            </tr>
        </table>
    </form>
</body>
</html>
```
#### Evaluation.aspx.cs
``` c#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Web;
using System.Web.UI;
using System.Web.UI.WebControls;

    public partial class Evaluation : System.Web.UI.Page
    {
        protected void Page_Load(object sender, EventArgs e) { }
    protected void BtnCal_Click1(object sender, EventArgs e)
    {
double dScore = double.Parse(txtScore.Text);
            if (dScore >= 90) { lblEvaluation.Text = "학점 : A"; }
            else if (dScore >= 80) { lblEvaluation.Text = "학점 : B"; }
            else if (dScore >= 70) { lblEvaluation.Text = "학점 : C"; }
            else if (dScore >= 60) { lblEvaluation.Text = "학점 : D"; }
            else { lblEvaluation.Text = "학점 : F"; }
    }
}
```
### 실행결과
![image](https://github.com/gryrryfh/web-programming/assets/50912987/2eff1ce0-32ba-4b0d-b935-941cf3951c42)
![image](https://github.com/gryrryfh/web-programming/assets/50912987/cb3722ee-7e1c-4c8c-a7c7-2175fb676543)
![image](https://github.com/gryrryfh/web-programming/assets/50912987/961e28a6-135e-49a5-9e8a-8984bf652bcf)
![image](https://github.com/gryrryfh/web-programming/assets/50912987/5b545c7b-039f-44f1-9e8b-928bfb563096)
![image](https://github.com/gryrryfh/web-programming/assets/50912987/52fafe49-54ba-4022-b732-0ee7efe11c07)

