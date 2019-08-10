# Documentation Summary

Payment System Api 

Demo:https://demo.paybank.com/


  <script src="https://www.paybank.com/payserver/jquery.min.js"></script>
  <script src="https://www.paybank.com/payserver/payment.min.js"></script>
  
  
 
var post_data = "";
  var post_json = "";
  var api_server = "server.php"; //demo php code   ->  editcode

  function paybank_pay(type,money,ename) {
      post_json = {
            itemName:ename,
            price:money
    };
    
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
    
