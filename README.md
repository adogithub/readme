# Lender Simulator (LS)

The LenderSimulator (LS) provides a WSDL endpoint able to accept requests and generate responses whose behaviour is configurable by means of a extensible configuration files. 

The very first endpoint selected is Fortiva, the LS allows the QLOL decision engine to build the requests. 
The LS supports proxying requests to the actual Fortiva endpoint(s) if a flag is set.
The configuration of the LS can be easily modified by means of the configuratin matrix, described below, by combining a lender, lookup fields and lookup values per request type.  
The LS make easier to introduce new lenders, request types and configurations of responses. 

The ultimate design an URL schema will follow this schema http://lendersimulator/{lender_name}/{request_type} fashion.

## Configuration
The behavior of the LS is governed by a series of rules. Each rule has a left- hand side (LHS, conditions) and a right-hand side (RHS, actions). In this context the LHS matches the content of the message with specific values to determine whether conditions match certain expectations. Once a expectation is matched then the appropriate action is triggered, in this case, a proper response is created with an optional latency. Therefore, the LS is determined by two configuration files: one to parse the request and one to create the response.
