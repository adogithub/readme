# Lender Simulator (LS) #

The ***LenderSimulator (LS)*** provides a WSDL endpoint able to accept requests and generate responses whose behaviour is configurable by means of a extensible configuration files. 

The very first endpoint selected is Fortiva, the ***LS*** allows the **QLOL** decision engine to build the requests. 
The LS supports proxying requests to the actual Fortiva endpoint(s) if a flag is set.
The configuration of the LS can be easily modified by means of the configuratin matrix, described below, by combining a lender, lookup fields and lookup values per request type.  
The LS make easier to introduce new lenders, request types and configurations of responses. 

The ultimate design an URL schema will follow this schema *http://lendersimulator/{lender_name}/{request_type}*

## Configuration
The behavior of the ***LS*** is governed by a series of rules. Each rule has a **left-hand-side** (LHS, conditions) and a **right-hand-side** (RHS, actions). In this context the LHS matches the content of the message with specific values to determine whether the conditions match certain expectations. Once a expectation is matched then the appropriate action is triggered, in this case, a proper response is created with an optional latency. Therefore, the ***LS*** is determined by *two configuration files*: one to parse the request and one to create the response.
The main construct behind the ability of the ***LS*** to accomodate a variety of behaviours is the Validations Matrix

### Validations Matrix

The ***Validations Matrix*** is structured as follows: For each combination of (1) *Request Type*; (2) *Field Name* and (3) *Lender* a specific *Field Value* that needs to be satisfied must be set.

The field values can be of three different kinds:

Field Type     | Description
-------------  | -------------
ExpectedValue  | Is a literal that needs to exactly match the corresponding entry provided in the request.
InListValue    | Similar to ExpectedValue, but this time the constant is in the shape of a List. This is useful to stabish a range of valid values.
ComputationValue | This is a complex type that is comprised by a constant and an operation. 

#### Examples of field types
```
    "lookup.fields.names": [
      {
        "code": "leadGen",
        "xpath": "clientInfo.leadGenName"
      },
      {
        "code": "language",
        "xpath": "clientInfo.language"
      }
´´´

The ***Validations Matrix*** fulfils its purpose because it contains the proper configuration of each request type for each field name per lender; It's easy to include a new lender, request type or field name, since that would only imply adding a row or column to the matrix. It is flexible for different types of requests and lenders since, although all fields need to be filled, we can select the required fields for each Request Type of each Lender. Below a schematic picture of the Validations Matrix.




