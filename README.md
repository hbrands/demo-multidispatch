## demo-multidispatch
Demo project to show Spring Boot working with multiple dispatcher servlets.
Currently, not all @SpringBootTest tests run.

## Structure
Basically, it's a standard Spring Boot Application with Autoconfiguration and Web, Security starters.
There is a DefaultController as RestController registered with the default dispatcher servlet.
See package com.example.demo.

What's special is, that in the WebConfig configuration class an additional DispatcherServlet is registered.
This dispatcher servlet has its own application context RestServletConfig.
This config finds per ComponentScan additional RestControllers like the WebController.
This RestServletConfig could also include additional bean defs, but that's not important here.
See package com.example.web.

This application seems to run fine.

The @SpringBootTest tests for the DefaultController also run fine.

What's not working is a test for the WebController (WebControllerTests#helloAuthorized()). 
When the test user is authenticated/authorized, I get a 404 error instead of the expected 200 status.

## open questions

- Am I doing something wrong or am I missing something?

- Is @SpringBootTest supposed to work with multiple dispatcher servlets? If yes, how?
