## 실핼결과

![image](https://github.com/gryrryfh/web-programming/assets/50912987/39786d7a-d2cb-4520-a87a-b9fc750b28de)

https://github.com/gryrryfh/web-programming/assets/50912987/51fa4a28-de35-4f72-a0b8-b3bab46b0481

![image](https://github.com/gryrryfh/web-programming/assets/50912987/8d9c1e20-03ed-4244-bbb8-f5d199b39631)

## 코드
#### ShoppingBasket.aspx
``` html
<%@ Page Language="C#" AutoEventWireup="true" CodeFile="ShoppingBasket.aspx.cs" Inherits="ShoppingBasket" %>

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">

<html xmlns="http://www.w3.org/1999/xhtml">
<head runat="server">
    <title></title>
    <style type="text/css">
        .style1
        {
            width: 24px;
        }
        .style2
        {
            width: 368px;
        }
        .style3
        {
            width: 24px;
            height: 39px;
        }
        .style4
        {
            width: 368px;
            height: 39px;
        }
        .style5
        {
            height: 39px;
        }
        .style6
        {
            height: 23px;
        }
        .style7
        {
            height: 98px;
        }
    </style>
</head>
<body>
    <form id="form1" runat="server">
    <div>
    
        <asp:Label ID="lblSessionInfo" runat="server"></asp:Label>
        <br />
        <br />
        <div style="border-style: solid; border-width: thin">
            <table style="width:100%;">
                <tr>
                    <td class="style3">
                        </td>
                    <td class="style4">
                        장바구니 보기</td>
                    <td class="style5">
                        </td>
                </tr>
                <tr>
                    <td class="style1">
                        &nbsp;</td>
                    <td class="style2">
                        <asp:ListBox ID="lstGoods" runat="server" Height="128px" Width="348px">
                        </asp:ListBox>
                    </td>
                    <td>
                        <table style="width: 100%; height: 116px;">
                            <tr>
                                <td class="style6">
                                    <asp:Button ID="btnMoreInfo" runat="server" onclick="btnMoreInfo_Click" 
                                        Text="상세 정보 보기" />
                                </td>
                            </tr>
                            <tr>
                                <td class="style7">
                                    <asp:Label ID="lblGoodsInfo" runat="server"></asp:Label>
                                </td>
                            </tr>
                        </table>
                    </td>
                </tr>
                <tr>
                    <td class="style1">
                        &nbsp;</td>
                    <td class="style2">
                        &nbsp;</td>
                    <td>
                        &nbsp;</td>
                </tr>
            </table>
        </div>
        <br />
    </div>
    </form>
</body>
</html>


```
#### ShoppingBasket.aspx.cs
```c#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Web;
using System.Web.UI;
using System.Web.UI.WebControls;

public partial class ShoppingBasket : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        /*
        Application.Lock();

        int count = 0;
        if (Application["HitCounterShoppingBasketPage"] != null)
        {
            count = (int)Application["HitCounterShoppingBasketPage"];
        }

        count++;

        Application["HitCounterShoppingBasketPage"] = count;

        Application.UnLock();
        lblSessionInfo.Text = "HitCount : " + count.ToString();
        */

        if (!IsPostBack)
        {
            Goods book1 = new Goods("Head First C#", "한빛미디어", 32000);
            Goods book2 = new Goods("Effective C#", "한빛미디어", 20000);
            Goods book3 = new Goods("데이터베이스 관리와 실습", "한빛미디어", 25000);

            Session["Book1"] = book1;
            Session["Book2"] = book2;
            Session["Book3"] = book3;

            lstGoods.Items.Add(book1.Name);
            lstGoods.Items.Add(book2.Name);
            lstGoods.Items.Add(book3.Name);
        }

        lblSessionInfo.Text = "세션 ID : " + Session.SessionID;
        lblSessionInfo.Text += "<br />세션 내 객체 개수 : " + Session.Count.ToString();
        lblSessionInfo.Text += "<br />세션 모드 : " + Session.Mode.ToString();
        lblSessionInfo.Text += "<br />쿠키 사용 안함 : " + Session.IsCookieless.ToString();
        lblSessionInfo.Text += "<br />새 세션 : " + Session.IsCookieless.ToString();
        lblSessionInfo.Text += "<br />세션 만료 시간 : " + Session.Timeout.ToString() + "분";
    }
    protected void btnMoreInfo_Click(object sender, EventArgs e)
    {
        if (lstGoods.SelectedIndex == -1)
        {
            lblGoodsInfo.Text = "장바구니에 있는 상품을 먼저 선택하세요.";
        }
        else
        {
            string key = "Book" + (lstGoods.SelectedIndex + 1).ToString();
            Goods book = (Goods)Session[key];

            lblGoodsInfo.Text = "도서명 : " + book.Name;
            lblGoodsInfo.Text += "<br />출판사 : " + book.Manufacturer;
            lblGoodsInfo.Text += "<br />정가 : " + book.Cost;
        }
    }
}
```
### goods.cs
``` c#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Web;

/// <summary>
/// Goods의 요약 설명입니다.
/// </summary>
[Serializable]
public class Goods
{
    public string Name;
    public string Manufacturer;
    public int Cost;
    public Goods(string name, string manufacturer, int cost)
    {
        Name = name;
        Manufacturer = manufacturer;
        Cost = cost;
    }
}
```
