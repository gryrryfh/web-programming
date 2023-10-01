## 4-1
![image](https://github.com/gryrryfh/web-programming/assets/50912987/d1742353-895e-4c10-b5b2-efa4114054fa)

## 4-2
## 코드
```html
<%@ Page Language="C#" AutoEventWireup="true" CodeFile="1.aspx.cs" Inherits="_1" %>

<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml">
<head runat="server">
<meta http-equiv="Content-Type" content="text/html; charset=utf-8"/>
    <title>체질량지수 산출기</title></head>
<body>
    <form id="WebForm" runat="server">
        <div align="center">
            신장 :&nbsp;
            <input id="Height" type="text" runat="server" />
            &nbsp;cm&nbsp;&nbsp;&nbsp;몸무게 :&nbsp;
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

public partial class _1 : System.Web.UI.Page
{
    protected void Calc_ServerClick(object sender, EventArgs e)
    {
        decimal height = Decimal.Parse(Height.Value) / 100;
        decimal weight = Decimal.Parse(Weight.Value);
        decimal BMI = weight / (height * height);
        Result.InnerText = "체질량지수(BMI) : " + BMI.ToString();
    }

}
```

## 실행결과
![image](https://github.com/gryrryfh/web-programming/assets/50912987/bad8f864-7dd2-43ab-93de-97d134f75d06)
