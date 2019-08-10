# Documentation Summary

Payment System Api 

Demo:https://demo.paybank.com/

<head>
  <script src="https://www.paybank.com/payserver/jquery.min.js"></script>
  <script src="https://www.paybank.com/payserver/payment.min.js"></script>
</head>
  


    var api_server = server.php
    
    var post_json = {
            itemName:ename,
            price:money
    }
    
    $.post(api_server,post_json,
        function(data,status){
          console.log(data);
          var obj = JSON.parse(data); 
          if(obj.sign)
           {
          action_pay(data);
        }else{
        alert('fail');
        }
       });
    }
    

