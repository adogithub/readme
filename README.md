# Lender Simulator (LS)

The LenderSimulator (LS) provides an WSDL endpoint for different lenders, the very first one is Fortiva. 


## Configuration
The behavior of the LS is governed by a series of rules. Each rule has a left- hand side (LHS, conditions) and a right-hand side (RHS, actions). In this context the LHS matches the content of the message with specific values to determine whether conditions match certain expectations. Once a expectation is matched then the appropriate action is triggered, in this case, a proper response is created with an optional latency. Therefore, the LS is determined by two configuration files: one to parse the request and one to create the response.
