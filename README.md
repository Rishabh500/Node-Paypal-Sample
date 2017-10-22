## Node-Paypal-Sample
This is sample for using paypal payment api with node-express 

# Usage
*1. Create a new sandbox business account from https://www.sandbox.paypal.com

*2. Add PayPal-node-SDK ("https://github.com/paypal/PayPal-Java-SDK")
     ```js
    var paypal = require('paypal-rest-sdk');
    ```
    
*3. Create config options, with parameters (mode, client_id, secret).
    ```js
    paypal.configure({
      'mode': 'sandbox', //sandbox or live
      'client_id': 'EBWKjlELKMYqRNQ6sYvFo64FtaRLRR5BdHEESmha49TM',
      'client_secret': 'EO422dn3gQLgDbuwqTjzrFgFtaRLRR5BdHEESmha49TM'
    });
    ```
    
*4.  Invoke the rest api (eg: create a PayPal payment) with required parameters (eg: data, config_options, callback).
    ```js
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

