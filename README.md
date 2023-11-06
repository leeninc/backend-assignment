# Leen Take Home Assessment

## Overview
This take home assessment's main goal is to give you an opportunity to showcase your skills and abilities 
outside a traditional interview setting. We want to see how you approach a problem and how you solve it. The problem is
an example of a real world problem that we face at Leen.

## Problem
We want to be able to quickly enrich an IP address with geo information. The goal is to design a service that provides
this information in a performant and scalable way. The service should have a web API interface that accepts an IP address
and returns the geo information in structured JSON.

Additionally, we will use this geo information to drive a feature for our product updates service. Given a user email 
and an IP address we will store the country they are in. We will use this information to send targeted product 
updates to users. 

## Requirements
The API should have at least 3 endpoints:
- GET `/ip/{ip_address}` - returns the geo information for the given IP address
  - ```json
    {
      "country_code": "US",
      "state": "California", \\ state1 and state2 combined ex. State1, State2 if both are present
      "city": "San Francisco",
      "postal_code": "94107",
      "timezone": "America/Los_Angeles",
    }
  
- POST `/subscribe` - subscribes a user to product updates. Accept the following body
  - ```json 
    {
      "email": "neel@leen.dev",
      "ip_address": "1.1.1.1"
    }  
- GET `/subscribe/{email}` - returns the following geo information for the given email address
  - ``` json
    {
      "country_code": "US"
      "timezone": "America/Los_Angeles"
    }
- Use the following file [geo-city-ipv4.csv.gz](geo-city-ipv4.csv.gz) containing the IP <> Geo mapping
  - a row is formatted in the following way
  - ```csv
    "ip_range_start, ip_range_end, country_code, state1, state2, city, postcode, latitude, longitude, timezone"```
    216.169.129.0,216.169.129.255,US,California,,San Francisco,94142,37.7809,-122.4245,America/Los_Angeles
- if any row information is missing, please return an empty string for that field
- include any database DDL if needed
- the service can be written in any language
- any data store can be used
- the service should be containerized so that we can run it locally. Please include any instructions to successfully run the service

** Bonus points **
- Provide a mechanism to update the static geo information given a new zip file.


Overall there are no limits on how you can go about solving this. Just please make sure the solution is able to run via docker.

## Assessment
We will assess your submission based on the following criteria:
- Completeness and correctness of the solution
- Code quality and readability
- Design and architecture
- Documentation

## Submission
1) Fork this repo and invite @neel-leendev with your completed solution. 
2) Include a link in the README with a short video 3-5 min explaining your solution. I recommend using [Loom](https://www.loom.com/) to record your video.
3) Shoot me an email when you are ready for me to review your submission.


Please don't hesitate to reach out if you have any questions. Good luck!