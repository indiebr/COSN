# COSN

## Supplier/Product API

### OrderProduct(product, quantity, brand and price range) 
* Response: int (quantity of product)
* Operation: Iterate over SupplierGallery until a Supplier that offers the desired product is found, ther return quantity, brand and price. If no such Supplier is found, return 0.

### RegisterSupplier(supplier info, list of products with quantities)
* Response: string (authentication token or empty string if fail)
* Operation: Create new Supplier with supplier info provided and add to SupplierGallery. Call on Authentication service to generate token for new Supplier. Return generated token.
* **Required interfaces**: GenerateSupplierToken(supplier id) [From Authentication service]
  
### AddProduct(product, quantity, brand, price, supplier id, authentication token)
* Response: bool (success/fail)
* Operation: Send supplier id and authentication token to Authentication service to authenticate supplier. Add Product to Supplier's list of Products
* **Required interfaces**: AuthenticateSupplier(supplier id, authentication token) [From Authentication service]

### RemoveProduct(product, quantity, brand, price, supplier id, authentication token)
* Response: bool (success/fail)
* Operation: Send supplier id and authentication token to Authentication service to authenticate supplier. Remove Product from Supplier's list of Products
* **Required interfaces**: AuthenticateSupplier(supplier id, authentication token) [From Authentication service]
