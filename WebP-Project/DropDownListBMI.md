## 코드
```html
<%@ Page Language="C#" AutoEventWireup="true" CodeFile="BMI.aspx.cs" Inherits="BMI" %>

<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml">
<head runat="server">
<meta http-equiv="Content-Type" content="text/html; charset=utf-8"/>
    <title>체질량지수 산출기</title>
    <style type="text/css">
        .auto-style1 {
            width: 125px;
        }
    </style>
</head>
<body>
    <form id="WebForm" runat="server">
        <div align="center">
            신장 :&nbsp;
            <input id="Height" type="text" runat="server" />
            &nbsp;<select id="Measure" runat="server" class="auto-style1" />
            &nbsp;&nbsp;&nbsp;몸무게 :&nbsp;
            <input id="Weight" type="text" runat="server" />
            &nbsp;kg
            <br /><br />
           <input id="Calc" type="submit" value="산출하기" OnServerClick="Calc_ServerClick" runat="server" />
            <br /><br />
        </div>
        <p id="Result" runat="server"></p>
    </form>
</body>
</html>

```
```c#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Web;
using System.Web.UI;
using System.Web.UI.WebControls;

public partial class BMI : System.Web.UI.Page
{
    protected void Calc_ServerClick(object sender, EventArgs e)
    {
        ListItem item = Measure.Items[Measure.SelectedIndex];
        decimal height = Decimal.Parse(Height.Value) * Decimal.Parse(item.Value);
        decimal weight = Decimal.Parse(Weight.Value);
        decimal BMI = weight / (height * height);
        Result.InnerText = "체질량지수(BMI) : " + BMI.ToString();
    }


    protected void Page_Load(object sender, EventArgs e)
    {
        if(!IsPostBack)
        {
            Measure.Items.Add(new ListItem("센티미터(cm)", "0.01"));
            Measure.Items.Add(new ListItem("피트(feet)", "0.3048"));
            Measure.Items.Add(new ListItem("미터(m)", "1"));
        }
    }
}
```
## 실행결과
### 적용하지 않은 페이지

  
### IsPostBack속성을 적용한 것
![image](https://github.com/gryrryfh/web-programming/assets/50912987/1f45a12a-70fe-4b20-9833-c292273d5ab6)

