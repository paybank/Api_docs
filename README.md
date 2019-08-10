# Documentation Summary

Payment System Api 



<head>
  <script src="https://www.paybank.com/payserver/jquery.min.js"></script>
  <script src="https://www.paybank.com/payserver/payment.min.js"></script>
</head>
  


<body>
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
          action_pay(data);
        }else{
        alert('fail');    
        }
       });
    }
  </body>  

Demo:https://demo.paybank.com/
