## Node-Paypal-Sample
This is sample for using paypal payment api with node-express 

# Usage
* Create a new sandbox business account from https://www.sandbox.paypal.com

* Add PayPal-node-SDK ("https://github.com/paypal/PayPal-Java-SDK")
    
    ```
    var paypal = require('paypal-rest-sdk');
    ```
    
* Create config options, with parameters (mode, client_id, secret).
   
   ```
    paypal.configure({
      'mode': 'sandbox', //sandbox or live
      'client_id': 'EBWKjlELKMYqRNQ6sYvFo64FtaRLRR5BdHEESmha49TM',
      'client_secret': 'EO422dn3gQLgDbuwqTjzrFgFtaRLRR5BdHEESmha49TM'
    });
    ```
    
* Invoke the rest api (eg: create a PayPal payment) with required parameters (eg: data, config_options, callback).
   
   
   ```
   paypal.payment.create(create_payment_json, function (error, payment) {
   if (error) {
       console.log(error);
    } else {
       for(let i = 0;i < payment.links.length;i++){
          if(payment.links[i].rel === 'approval_url'){
           res.redirect(payment.links[i].href);
           }
          }
       }
    });
    ```

