# Online Store Checkout Product Success

1. Collection Pre-request

   ```js
   const data = {
     keyword: 'Bicycle',
     product_name: 'Balance Training Bicycle',
     product_id: 1,
     order: {
       cart: [
         {
           product_id: 1,
           quantity: 1,
         },
       ],
       burn_point: 0,
     },
   };

   const keys = _.keys(data);

   // keys.forEach( (e) => console.log(e) );

   // console.log(data[keys[3]]);

   const dataKeys = _.keys(pm.iterationData.toObject());
   const missingKeys = keys.filter((key) => !dataKeys.includes(key));
   // missingKeys.forEach( (e) => console.log(data[e]) );
   missingKeys.forEach((k) => pm.variables.set(k, data[k]));
   ```

2. search-product: Post-response

   ```js
   pm.test(
     'ต้องมีสินค้าที่มีชื่อ ' + pm.variables.get('product_name'),
     function () {
       var jsonData = pm.response.json();
       pm.expect(jsonData.products[0].product_name).to.eql(
         pm.variables.get('product_name')
       );
     }
   );
   ```
