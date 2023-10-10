```html
<%@ Page Language="C#" AutoEventWireup="true" CodeFile="CoffeeRecipe.aspx.cs" Inherits="CoffeeRecipe" %>

<!DOCTYPE html>

<html xmlns="http://www.w3.org/1999/xhtml">
<head runat="server">
<meta http-equiv="Content-Type" content="text/html; charset=utf-8"/>
    <title></title>
    <style type="text/css">
        .auto-style2 {
            height: 114px;
        }
    </style>
</head>
<body>
    <form id="CoffeeForm" runat="server">
        <div class="auto-style2">
            <br />
            <br />
            커피 종류 선택 :
            <select id="CoffeeType" name="D1" runat="server">
                <option></option>
            </select>
            <input id="ShowRecipe" type="submit" value="조리법 보기"  runat="server" onserverclick="Show_ServerClick" /></div>
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

public partial class CoffeeRecipe : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        if (!IsPostBack)
        {
            CoffeeType.Items.Clear();
            CoffeeType.Items.Add(new ListItem("밀크커피(설탕+프림", "0"));
            CoffeeType.Items.Add(new ListItem("프림커피(프림)", "1"));
            CoffeeType.Items.Add(new ListItem("설탕커피(설탕)", "2"));
            CoffeeType.Items.Add(new ListItem("블랙커피", "3"));
        }
    }
    protected void Show_ServerClick(object sender, EventArgs e)
    {
        string filePath = Request.PhysicalApplicationPath + @"App_Data\";
        string fileName = "";
        Response.Write("<ol>");
        ListItem item = CoffeeType.Items[CoffeeType.SelectedIndex];
        int coffeeType = int.Parse(item.Value);
        for (int i = 0; i < 4; i++)
        {
            fileName = filePath + i + ".txt";
            Response.WriteFile(fileName);
            if (i != 3 && ((i & coffeeType) == 1 || (i & coffeeType) == 2))Response.Clear();
            Response.Flush();
        }
        Response.Write("</ol>");



    }
}
```
```c#
<%@ Application Language="C#" %>

<script runat="server">

    void Application_Start(object sender, EventArgs e) 
    {
        // 애플리케이션 시작 시 실행되는 코드

    }
    
    void Application_EndRequest(object sender, EventArgs e) 
    {
        Response.Write("<hr />");
        Response.Write("이 페이지는 ");
        Response.Write(DateTime.Now.ToString());
        Response.Write("에 작성되었습니다.");
        //  애플리케이션 종료 시 실행되는 코드

    }
        
    void Application_Error(object sender, EventArgs e) 
    { 
        // 처리되지 않은 오류 발생 시 실행되는 코드

    }

    void Session_Start(object sender, EventArgs e) 
    {
        // 새 세션이 시작할 때 실행되는 코드입니다.

    }

    void Session_End(object sender, EventArgs e) 
    {
        // 세션이 끝날 때 실행되는 코드입니다. 
        // 참고: Session_End 이벤트는 Web.config 파일에서 sessionstate 모드가
        // InProc로 설정되어 있는 경우에만 발생합니다. 세션 모드가 StateServer 또는 SQLServer로 
        // 설정되어 있는 경우에는 이 이벤트가 발생하지 않습니다.

    }
       
</script>

```
![image](https://github.com/gryrryfh/web-programming/assets/50912987/e946d0a4-62ef-4493-a899-0caa4ccc13b0)

![image](https://github.com/gryrryfh/web-programming/assets/50912987/4da2f06d-6f92-41a3-9dd9-4166cee25fee)
![image](https://github.com/gryrryfh/web-programming/assets/50912987/a5a4b71a-20ae-4bc7-9ab2-b82ace7faa76)

![image](https://github.com/gryrryfh/web-programming/assets/50912987/596b8aba-a686-4003-8ace-21ed7b6daa9e)

![image](https://github.com/gryrryfh/web-programming/assets/50912987/632db916-b61d-4c9f-b3cc-5eef29cb9a92)

![image](https://github.com/gryrryfh/web-programming/assets/50912987/ca01a8a3-2d07-4941-abfc-db0b79e90155)
![image](https://github.com/gryrryfh/web-programming/assets/50912987/6321656c-20fe-44b4-aada-4bf368888414)
![image](https://github.com/gryrryfh/web-programming/assets/50912987/71e5ae82-7320-4782-881b-b1ecc4c78970)




