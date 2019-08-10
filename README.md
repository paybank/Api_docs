# Documentation Summary

Request signature
Request signature, all parameter pairs are sorted in ascending order by dictionary (abcd ...), and the secret assigned by the platform is the key. First, all parameters except the signature itself need to be added in the format "KEY = value" and use the character "&". Add the exact order of the request, then use md5 to encrypt the generated string and then lowercase it. Note: The sign parameter does not participate in the signature; the null parameter does not participate in the signature.

qrcode
QrcodeURI: Local generation

Parameters Description

<table>
<thead>
<tr>
<th>Parameter</th>
<th>Description</th>
<th>Type</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr>
<td>amount</td>
<td>Legal currency amount (up to 2 decimal places)
</td>
<td>BigDecimal</td>
<td>Yes</td>
</tr>
<tr>
<td>appKey</td>
<td>Legal currency amount (up to 2 decimal places)
</td>
<td>BigDecimal</td>
<td>Yes</td>
</tr>
<tr>
<td>currencyType</td>
<td>Legal currency amount (up to 2 decimal places)
</td>
<td>goodsName</td>
<td>Yes</td>
</tr>
<tr>
<td>merchantOrderNum</td>
<td>Merchant order number
</td>
<td>String</td>
<td>Yes</td>
</tr>
<tr>
<td>qrCodeType</td>
<td>QR code type (fixed 1)
</td>
<td>Int</td>
<td>Yes</td>
</tr>
<tr>
<td>ts</td>
<td>Current timestamp (seconds)
</td>
<td>Long</td>
<td>Yes</td>
</tr>
<tr>
<td>sign</td>
<td>Used for integrity verification, Querystring('AMOUNT=99.88&APPKEY=appKey&CURRENCYTYPE=1&GOODSNAME=testName&MERCHANTORDERNUM=20190712001&QRCODETYPE=1&TS='Date.parse(new Date())/1000'&APPSECRET=appSecret') string; Note: Enter the variables in md5 in alphabetical order, as shown in the example,Replace appSecret with the merchant's appSecret string

</td>
<td>String</td>
<td>Yes</td>
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
