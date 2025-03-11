# Online Store Checkout Product Success

1. Collection PreScript

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
