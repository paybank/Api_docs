# Documentation Summary

Request signature
Request signature, all parameter pairs are sorted in ascending order by dictionary (abcd ...), and the secret assigned by the platform is the key. First, all parameters except the signature itself need to be added in the format "KEY = value" and use the character "&". Add the exact order of the request, then use md5 to encrypt the generated string and then lowercase it. Note: The sign parameter does not participate in the signature; the null parameter does not participate in the signature.

qrcode
QrcodeURI: Local generation

Parameters Description

<table>
<thead>
<tr>
<th>接口</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr>
<td><a href="https://github.com/huobiapi/API_Docs/wiki/REST_api_reference#post-v1orderordersplace-pro%E7%AB%99%E4%B8%8B%E5%8D%95">POST /v1/order/orders/place</a></td>
<td>创建并执行订单</td>
</tr>
<tr>
<td><a href="https://github.com/huobiapi/API_Docs/wiki/REST_api_reference#post-v1orderordersorder-idsubmitcancel--%E7%94%B3%E8%AF%B7%E6%92%A4%E9%94%80%E4%B8%80%E4%B8%AA%E8%AE%A2%E5%8D%95%E8%AF%B7%E6%B1%82">POST /v1/order/orders/{order-id}/submitcancel</a></td>
<td>撤销一个订单</td>
</tr>
<tr>
<td><a href="https://github.com/huobiapi/API_Docs/wiki/REST_api_reference#post-v1orderordersbatchcancel-%E6%89%B9%E9%87%8F%E6%92%A4%E9%94%80%E8%AE%A2%E5%8D%95">POST /v1/order/orders/batchcancel</a></td>
<td>批量撤销订单</td>
</tr>
<tr>
<td><a href="https://github.com/huobiapi/API_Docs/wiki/REST_api_reference#post--v1orderordersbatchcancelopenorders--%E6%89%B9%E9%87%8F%E5%8F%96%E6%B6%88%E7%AC%A6%E5%90%88%E6%9D%A1%E4%BB%B6%E7%9A%84%E8%AE%A2%E5%8D%95">POST /v1/order/orders/batchCancelOpenOrders</a></td>
<td>撤销当前委托订单</td>
</tr>
<tr>
<td><a href="https://github.com/huobiapi/API_Docs/wiki/REST_api_reference#get-v1orderordersorder-id-%E6%9F%A5%E8%AF%A2%E6%9F%90%E4%B8%AA%E8%AE%A2%E5%8D%95%E8%AF%A6%E6%83%85">GET /v1/order/orders/{order-id}</a></td>
<td>查询一个订单详情</td>
</tr>
<tr>
<td><a href="https://github.com/huobiapi/API_Docs/wiki/REST_api_reference#get-v1orderorders-%E6%9F%A5%E8%AF%A2%E5%BD%93%E5%89%8D%E5%A7%94%E6%89%98%E5%8E%86%E5%8F%B2%E5%A7%94%E6%89%98">GET /v1/order/orders</a></td>
<td>查询当前委托、历史委托</td>
</tr>
<tr>
<td><a href="https://github.com/huobiapi/API_Docs/wiki/REST_api_reference#get-v1orderopenorders-%E8%8E%B7%E5%8F%96%E6%89%80%E6%9C%89%E5%BD%93%E5%89%8D%E5%B8%90%E5%8F%B7%E4%B8%8B%E6%9C%AA%E6%88%90%E4%BA%A4%E8%AE%A2%E5%8D%95">GET /v1/order/openOrders</a></td>
<td>查询当前委托订单</td>
</tr>
<tr>
<td><a href="https://github.com/huobiapi/API_Docs/wiki/REST_api_reference#get-v1ordermatchresults-%E6%9F%A5%E8%AF%A2%E5%BD%93%E5%89%8D%E6%88%90%E4%BA%A4%E5%8E%86%E5%8F%B2%E6%88%90%E4%BA%A4">GET /v1/order/matchresults</a></td>
<td>查询成交</td>
</tr>
<tr>
<td><a href="https://github.com/huobiapi/API_Docs/wiki/REST_api_reference#get-v1orderordersorder-idmatchresults--%E6%9F%A5%E8%AF%A2%E6%9F%90%E4%B8%AA%E8%AE%A2%E5%8D%95%E7%9A%84%E6%88%90%E4%BA%A4%E6%98%8E%E7%BB%86">GET /v1/order/orders/{order-id}/matchresults</a></td>
<td>查询某个订单的成交明细</td>
</tr>
<tr>
<td><a href="https://github.com/huobiapi/API_Docs/wiki/REST_api_reference#get-v1accountaccounts">GET /v1/account/accounts</a></td>
<td>查询当前用户的所有账户</td>
</tr>
<tr>
<td><a href="https://github.com/huobiapi/API_Docs/wiki/REST_api_reference#get-v1accountaccountsaccount-idbalance-%E6%9F%A5%E8%AF%A2pro%E7%AB%99%E6%8C%87%E5%AE%9A%E8%B4%A6%E6%88%B7%E7%9A%84%E4%BD%99%E9%A2%9D">GET /v1/account/accounts/{account-id}/balance</a></td>
<td>查询指定账户的余额</td>
</tr>
</tbody>
</table>


--head--
  <script src="https://www.paybank.com/payserver/jquery.min.js"></script>
  
  <script src="https://www.paybank.com/payserver/payment.min.js"></script>
--head--
  
--body--

    var api_server = 'server.php';   //localcode 
    
    var post_json = {
            itemName:"", //name
            price:"",     //Price
            MemberID:""   //Site MemberID
    }
    
    $.post(api_server,post_json,
        function(data,status){
          console.log(data);
          var obj = JSON.parse(data); 
          if(obj.sign)
           {
          action_pay(data);   //paysystem function
        }else{
        alert('fail');    
        }
       });
    }
--body--

Demo:https://demo.paybank.com/
