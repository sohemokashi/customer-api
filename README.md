# Customer API

## API First Development
An API-first approach assumes the design and development of an application programming interface (API) comes before the implementation. Your team begins by creating an interface for their application. After the API has been developed, the team will rely on this interface to build the rest of the application.

## Swagger OpenAPI Specification
The OpenAPI Specification (OAS) defines a standard, language-agnostic interface to RESTful APIs which allows both humans and computers to discover and understand the capabilities of the service without access to source code, documentation, or through network traffic inspection. When properly defined, a consumer can understand and interact with the remote service with a minimal amount of implementation logic.

An OpenAPI definition can then be used by documentation generation tools to display the API, code generation tools to generate servers and clients in various programming languages, testing tools, and many other use cases.

Getting Started: [Swagger OpenAPI Specification](https://swagger.io/specification/)

## Customer API Design
Before proceeding with API Design, if you're not ready with localset up or use case, please click [here](https://github.com/acc-trainings/customer-api)

 ```
openapi: 3.0.0

info:
  title: "Customer API"
  version: "1.0.0"
  contact:
    name: Accenture
    email: contact@example.com
    url: https://example.com/

tags:
  - name: Customer API
    description: Customer Service related operations
    
paths:
  /customer/{id}:
    get:
      operationId: getCustomer
      parameters:
        - name: id
          in: path
          description: find customer
          required: true
          schema: 
            type: string
          
      summary: Get customer details
      tags: [ 'Customer API' ]
      responses:
        '200':
          description: OK
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/Customer'
        '500':
          description: Internal Server Error
        '404':
          description: Customer Not Found
        '400':
          description: Invalid ID supplied
          
  /createCustomer:
    post:
      description: Create Customer
      summary: Create Customer
      tags: [ 'Customer API' ]
      operationId: createCustomer
      requestBody:
        description: "Create Customer"
        content:
         application/json:
          schema:
            $ref: '#/components/schemas/Customer'   
      responses:
        '200':
          description: Customer Create Successfully
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/Customer'
        '500':
           description: Internal Server       

components:
  schemas:
    Customer:
      description: This is a customer model
      type: object
      required:
        - "customerId"
      properties:
        id:
          type: string
          description: Mongo document unique ID
          example: Generated by the application 
        customerId:
          type: string
          description: "Id of the customer"
          example: 12345
          minLength: 5
          maxLength: 8
        customerName:
          type: string
          description: Name of the customer
          example: Jessica Alba
        customerAddress:
          type: string
          description: Customer address
          example: 900 Main Street, 55 
```

Copy and paste the above code into [Swagger Editor](https://editor.swagger.io/) to visualize the API design. 
