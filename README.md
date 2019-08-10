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
<td>amount</td>
<td>Legal currency amount (up to 2 decimal places)
</td>
<td>BigDecimal</td>
<td>Yes</td>
</tr>
<tr>
<td>amount</td>
<td>Legal currency amount (up to 2 decimal places)
</td>
<td>BigDecimal</td>
<td>Yes</td>
</tr>
<tr>
<td>amount</td>
<td>Legal currency amount (up to 2 decimal places)
</td>
<td>BigDecimal</td>
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
