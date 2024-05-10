# Pactum.Js for API E2E Testing

![logo](../pix/viiinzzz48.png){: style="float: left"}
*Մι∩z•thedev* · [Follow](mailto:vinz.thedev@gmail.com)
Published in *Coding* · 6 min read · 1 day ago
___
<span style="font-size:2.5em">👏</span>65k <span style="font-size:2.5em">💬</span>321 <span style="font-size:2.5em">🔖</span> <span style="font-size:2.5em">⤴️</span>
___

![pactumjs](../pix/pactum-js.png)
## The project background

Bento Solidaires is one of my Javascript projects. The central activity is to forge deals between voluntary cook and guest. It's a dreamer project where money is not the token but reputation is. Together voluntaries may leverage a new kind of solidarity that would alleviate a sick societal model.

Here is the swim-lane view of what happens between actors chronologically :

![swimlane](../pix/bento1.png)

And here is the Finite State Machine at the heart of the deal :

![swimlane](../pix/bento2.png)

That kind of multiple step asynchronous process is sometimes called SAGA pattern.

As a conscientious dev, I felt the thing is prone to many forgotten side-case oblivions, so I decided to test meticulously the API with Jest as a test runner and a specialized API testing library called Pactum.js.

That 's the top part of the testing pyramid : End-to-End testing. It means all has been arranged earlier so that test databases are regenerated or that appropriate double are available. I chose test databases and some scripts to arrange the playground.

Time is a critical data in the transaction so the API must be able to fake it by design.

That said, I had an incremental coding process using hot-reload, so I wanted the test suite to run automatically, to quickly spot accomplishment or regression. In fact, it turned I had to pause it because E2E is pretty intensive. I just ran it regularly by myself (before commit for example)

Pactum is great but I extended it for what I imagined would be a great output transcript, as a proof the code works as expected, and as a documentation for new collaborators joining in.

Just like Hannibal Smith, "I love it when a plan comes together" is my so called nominal case. Well this is the start of the business, so that's the first one I tested. Let's read the transcript :

```

## √ let user do social cooking on Bento Solidaires

> Test run started at 5/10/2024, 10:28:28 AM <

 debug 
       «
       Jest 😃 Pactum😃
           + ✨  Vinz ✨ PactumHelper & JSON Schema
       = The 👌 perfect👌 API 🕵️  proofing🕵️  suite.
       »
       
 debug 
       «
        🕒 rev.1
       >Server says time is  Fri, 10 May 2024 08:28:51 GMT<
        Local  says time is  Fri, 10 May 2024 08:28:52 GMT
        expect/actual jitter +0ms / -1ms  delta +1ms
       »
       
 debug   REGISTRATION
       ┈┈┈┈┈┈┈┈┈┈┈┈┈┈
       «
        'Julius' registers as a new user on the web site 'Bento Solidaires'
       »
       
 info 
       ╭┈◜POST◝┈┈ 🟢 ┈┈( users/post )┈┈
       ┊                ┈┈>( users/post/response )┈┈┈┈┈┈
       ┊ 🕒 1558ms
       ┊ 🔑 anonymous
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊🗣️  Request
       ┊ = 
         method = POST
         url = http://localhost:7777/api/v1/user
         
         🔝 headers
          = 
           [0] = Content-Type: application/json
         
         📃 body
          = 
           first_name = Julius
           last_name = Holder-Tester
           email = Julius91.Holder@pacific.sea
           userId = T_HolderJ91
           password = Welcome123!
           confirm_password = Welcome123!
           locale = en-US
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊🪃  Response
       ┊ = 
         statusCode = 201
         
         🔝 headers
          = 
           [0] = date: Fri, 10 May 2024 08:28:51 GMT
           [1] = request-id: 22220@LAPTOP-7D28KH4S/4ed5a4cac14854af5405f2bb-0000000000000003
           [2] = content-security-policy: report-uri http://localhost:7777/cspreport/send?time=1715329731000;
           [3] = cross-origin-embedder-policy: same-origin
           [4] = cross-origin-opener-policy: same-origin
           [5] = cross-origin-resource-policy: same-site
           [6] = x-dns-prefetch-control: off
           [7] = expect-ct: max-age=0
           [8] = x-frame-options: SAMEORIGIN
           [9] = strict-transport-security: max-age=15552000; includeSubDomains
           [10] = x-download-options: noopen
           [11] = x-content-type-options: nosniff
           [12] = origin-agent-cluster: ?1
           [13] = x-permitted-cross-domain-policies: none
           [14] = referrer-policy: strict-origin-when-cross-origin
           [15] = x-xss-protection: 0
           [16] = access-control-allow-origin: *
           [17] = access-control-allow-methods: GET,PUT,POST,DELETE,OPTIONS
           [18] = access-control-allow-headers: Origin, X-Requested-With, Content-Type, Accept
           [19] = sec-fetch-dest: image
           [20] = sec-fetch-mode: no-cors
           [21] = sec-fetch-site: cross-site
           [22] = set-cookie: bento-Bearer=eyJhbGciOiJIUzUxMiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6IlRfSG9sZGVySjkxIiwibGFzdE5hbWUiOiJIb2xkZXItVGVzdGVyIiwiZmlyc3ROYW1lIjoiSnVsaXVzIiwicm9sZXMiOltdLCJpYXQiOjE3MTUzMjk3MzEsImV4cCI6MTcxNTkzNDUzMX0.sFb5ghCoscjnGZP7A11mTvF518pFa09f8ZCObulKZGjBFqcLiMhP9ywnvpRQ98kTrwuRlhnYmSWx75ofFsGO8w; Max-Age=604; Path=/; Expires=Fri, 10 May 2024 08:38:55 GMT; HttpOnly
           [23] = content-type: application/json; charset=utf-8
           [24] = content-length: 497
           [25] = etag: W/"1f1-ivzlpsQQFCTgiI5S2wHVIqC0jog"
           [26] = connection: close
         
         📃 body
          = 
           requestId = 22220@LAPTOP-7D28KH4S/4ed5a4cac14854af5405f2bb-0000000000000003
           token = eyJhbGciOiJIUzUxMiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6IlRfSG9sZGVySjkxIiwibGFzdE5hbWUiOiJIb2xkZXItVGVzdGVyIiwiZmlyc3ROYW1lIjoiSnVsaXVzIiwicm9sZXMiOltdLCJpYXQiOjE3MTUzMjk3MzEsImV4cCI6MTcxNTkzNDUzMX0.sFb5ghCoscjnGZP7A11mTvF518pFa09f8ZCObulKZGjBFqcLiMhP9ywnvpRQ98kTrwuRlhnYmSWx75ofFsGO8w
           inactive = true
           username = T_HolderJ91
           lastName = Holder-Tester
           firstName = Julius
           code = 826262
           result = success
       
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊👉 return = 
         requestId = 22220@LAPTOP-7D28KH4S/4ed5a4cac14854af5405f2bb-0000000000000003
         token = eyJhbGciOiJIUzUxMiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6IlRfSG9sZGVySjkxIiwibGFzdE5hbWUiOiJIb2xkZXItVGVzdGVyIiwiZmlyc3ROYW1lIjoiSnVsaXVzIiwicm9sZXMiOltdLCJpYXQiOjE3MTUzMjk3MzEsImV4cCI6MTcxNTkzNDUzMX0.sFb5ghCoscjnGZP7A11mTvF518pFa09f8ZCObulKZGjBFqcLiMhP9ywnvpRQ98kTrwuRlhnYmSWx75ofFsGO8w
         inactive = true
         username = T_HolderJ91
         lastName = Holder-Tester
         firstName = Julius
         code = 826262
         result = success
       
 debug 
       «
        Julius waits before activation...
       ⏰ fake sleep 45s
       »
       
 debug   ACTIVATION
       ┈┈┈┈┈┈┈┈┈┈┈┈
       «
        Julius attempts to activate his/her account with code '826262' received by email
       »
       
 info 
       ╭┈◜PUT◝┈┈ 🟢 ┈┈( users/put )┈┈
       ┊                ┈┈>( users/put/response )┈┈┈┈┈┈
       ┊ 🕒 181ms
       ┊ 🔑 Bearer
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊🗣️  Request
       ┊ = 
         method = PUT
         url = http://localhost:7777/api/v1/user/T_HolderJ91
         
         🔝 headers
          = 
           [0] = Content-Type: application/json
           [1] = authorization: Bearer eyJhbGciOiJIUzUxMiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6IlRfSG9sZGVySjkxIiwibGFzdE5hbWUiOiJIb2xkZXItVGVzdGVyIiwiZmlyc3ROYW1lIjoiSnVsaXVzIiwicm9sZXMiOltdLCJpYXQiOjE3MTUzMjk3MzEsImV4cCI6MTcxNTkzNDUzMX0.sFb5ghCoscjnGZP7A11mTvF518pFa09f8ZCObulKZGjBFqcLiMhP9ywnvpRQ98kTrwuRlhnYmSWx75ofFsGO8w
           [2] = mock-time-seconds: 45
         
         📃 body
          = 
           activation = 
             code = 826262
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊🪃  Response
       ┊ = 
         statusCode = 200
         
         🔝 headers
          = 
           [0] = date: Fri, 10 May 2024 08:29:36 GMT
           [1] = request-id: 22220@LAPTOP-7D28KH4S/4ed5a4cac14854af5405f2bb-0000000000000005
           [2] = content-security-policy: report-uri http://localhost:7777/cspreport/send?time=1715329776000;
           [3] = cross-origin-embedder-policy: same-origin
           [4] = cross-origin-opener-policy: same-origin
           [5] = cross-origin-resource-policy: same-site
           [6] = x-dns-prefetch-control: off
           [7] = expect-ct: max-age=0
           [8] = x-frame-options: SAMEORIGIN
           [9] = strict-transport-security: max-age=15552000; includeSubDomains
           [10] = x-download-options: noopen
           [11] = x-content-type-options: nosniff
           [12] = origin-agent-cluster: ?1
           [13] = x-permitted-cross-domain-policies: none
           [14] = referrer-policy: strict-origin-when-cross-origin
           [15] = x-xss-protection: 0
           [16] = access-control-allow-origin: *
           [17] = access-control-allow-methods: GET,PUT,POST,DELETE,OPTIONS
           [18] = access-control-allow-headers: Origin, X-Requested-With, Content-Type, Accept
           [19] = sec-fetch-dest: image
           [20] = sec-fetch-mode: no-cors
           [21] = sec-fetch-site: cross-site
           [22] = content-type: application/json; charset=utf-8
           [23] = content-length: 98
           [24] = etag: W/"62-Bhu27eNLIh4IvkWCXAPfui1icmE"
           [25] = connection: close
         
         📃 body
          = 
           requestId = 22220@LAPTOP-7D28KH4S/4ed5a4cac14854af5405f2bb-0000000000000005
           result = success
       
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊👉 return = 
         requestId = 22220@LAPTOP-7D28KH4S/4ed5a4cac14854af5405f2bb-0000000000000005
         result = success
       
 debug 
       «
        Julius is happy !
       He/she has registered and activated an account,
       meaning he/she can access the Bento Solidaires website and start contributing.
       »
       
 debug 
       «
        Julius's favorite ingredients are 'Nursehound', 'calabrese', 'new zealand spinach', 'Rabbit', 'black bean', 'shallot'
       »
       
 debug   PUBLISHING
       ┈┈┈┈┈┈┈┈┈┈┈┈
       «
        Julius is going to create them on Bento Solidaires.
       »
       
 debug 
       «
        Julius creates 'Nursehound' because he/she uses 'Nursehound' in his/her cooking.
       »
       
 info 
       ╭┈◜POST◝┈┈ 🟢 ┈┈( recipes/post/ingredient-post/id )┈┈
       ┊                ┈┈>( traits/post-response )┈┈┈┈┈┈
       ┊ 🕒 119ms
       ┊ 🔑 Bearer
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊🗣️  Request
       ┊ = 
         method = POST
         url = http://localhost:7777/api/v1/ingredient
         
         🔝 headers
          = 
           [0] = Content-Type: application/json
           [1] = authorization: Bearer eyJhbGciOiJIUzUxMiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6IlRfSG9sZGVySjkxIiwibGFzdE5hbWUiOiJIb2xkZXItVGVzdGVyIiwiZmlyc3ROYW1lIjoiSnVsaXVzIiwicm9sZXMiOltdLCJpYXQiOjE3MTUzMjk3MzEsImV4cCI6MTcxNTkzNDUzMX0.sFb5ghCoscjnGZP7A11mTvF518pFa09f8ZCObulKZGjBFqcLiMhP9ywnvpRQ98kTrwuRlhnYmSWx75ofFsGO8w
         
         📃 body
          = 
           name = Nursehound
           cost = 60
           cost_currency = EUR
           quantity = 1000
           unit = g
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊🪃  Response
       ┊ = 
         statusCode = 201
         
         🔝 headers
          = 
           [0] = date: Fri, 10 May 2024 08:29:36 GMT
           [1] = request-id: 22220@LAPTOP-7D28KH4S/4ed5a4cac14854af5405f2bb-0000000000000006
           [2] = content-security-policy: report-uri http://localhost:7777/cspreport/send?time=1715329776000;
           [3] = cross-origin-embedder-policy: same-origin
           [4] = cross-origin-opener-policy: same-origin
           [5] = cross-origin-resource-policy: same-site
           [6] = x-dns-prefetch-control: off
           [7] = expect-ct: max-age=0
           [8] = x-frame-options: SAMEORIGIN
           [9] = strict-transport-security: max-age=15552000; includeSubDomains
           [10] = x-download-options: noopen
           [11] = x-content-type-options: nosniff
           [12] = origin-agent-cluster: ?1
           [13] = x-permitted-cross-domain-policies: none
           [14] = referrer-policy: strict-origin-when-cross-origin
           [15] = x-xss-protection: 0
           [16] = access-control-allow-origin: *
           [17] = access-control-allow-methods: GET,PUT,POST,DELETE,OPTIONS
           [18] = access-control-allow-headers: Origin, X-Requested-With, Content-Type, Accept
           [19] = sec-fetch-dest: image
           [20] = sec-fetch-mode: no-cors
           [21] = sec-fetch-site: cross-site
           [22] = content-type: application/json; charset=utf-8
           [23] = content-length: 178
           [24] = etag: W/"b2-ex0JPC549xcDqJVRoG6zqbbmkYI"
           [25] = connection: close
         
         📃 body
          = 
           requestId = 22220@LAPTOP-7D28KH4S/4ed5a4cac14854af5405f2bb-0000000000000006
           id = MfZR5wDt5Bcy3p9P43yAgY
           url = /api/v1/ingredient/MfZR5wDt5Bcy3p9P43yAgY
           result = success
       
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊👉 return = MfZR5wDt5Bcy3p9P43yAgY
       
 debug 
       «
        Julius creates 'calabrese' because he/she uses 'calabrese' in his/her cooking.
       »
       
 info 
       ╭┈◜POST◝┈┈ 🟢 ┈┈( recipes/post/ingredient-post/id )┈┈
       ┊                ┈┈>( traits/post-response )┈┈┈┈┈┈
       ┊ 🕒 116ms
       ┊ 🔑 Bearer
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊🗣️  Request
       ┊ = 
         method = POST
         url = http://localhost:7777/api/v1/ingredient
         
         🔝 headers
          = 
           [0] = Content-Type: application/json
           [1] = authorization: Bearer eyJhbGciOiJIUzUxMiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6IlRfSG9sZGVySjkxIiwibGFzdE5hbWUiOiJIb2xkZXItVGVzdGVyIiwiZmlyc3ROYW1lIjoiSnVsaXVzIiwicm9sZXMiOltdLCJpYXQiOjE3MTUzMjk3MzEsImV4cCI6MTcxNTkzNDUzMX0.sFb5ghCoscjnGZP7A11mTvF518pFa09f8ZCObulKZGjBFqcLiMhP9ywnvpRQ98kTrwuRlhnYmSWx75ofFsGO8w
         
         📃 body
          = 
           name = calabrese
           cost = 60
           cost_currency = EUR
           quantity = 1000
           unit = g
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊🪃  Response
       ┊ = 
         statusCode = 201
         
         🔝 headers
          = 
           [0] = date: Fri, 10 May 2024 08:29:36 GMT
           [1] = request-id: 22220@LAPTOP-7D28KH4S/4ed5a4cac14854af5405f2bb-0000000000000007
           [2] = content-security-policy: report-uri http://localhost:7777/cspreport/send?time=1715329776000;
           [3] = cross-origin-embedder-policy: same-origin
           [4] = cross-origin-opener-policy: same-origin
           [5] = cross-origin-resource-policy: same-site
           [6] = x-dns-prefetch-control: off
           [7] = expect-ct: max-age=0
           [8] = x-frame-options: SAMEORIGIN
           [9] = strict-transport-security: max-age=15552000; includeSubDomains
           [10] = x-download-options: noopen
           [11] = x-content-type-options: nosniff
           [12] = origin-agent-cluster: ?1
           [13] = x-permitted-cross-domain-policies: none
           [14] = referrer-policy: strict-origin-when-cross-origin
           [15] = x-xss-protection: 0
           [16] = access-control-allow-origin: *
           [17] = access-control-allow-methods: GET,PUT,POST,DELETE,OPTIONS
           [18] = access-control-allow-headers: Origin, X-Requested-With, Content-Type, Accept
           [19] = sec-fetch-dest: image
           [20] = sec-fetch-mode: no-cors
           [21] = sec-fetch-site: cross-site
           [22] = content-type: application/json; charset=utf-8
           [23] = content-length: 178
           [24] = etag: W/"b2-mZSd8jSIw6JfszUBirwtcVWa4ug"
           [25] = connection: close
         
         📃 body
          = 
           requestId = 22220@LAPTOP-7D28KH4S/4ed5a4cac14854af5405f2bb-0000000000000007
           id = V4WtDJeJExC68HxdpQ77eS
           url = /api/v1/ingredient/V4WtDJeJExC68HxdpQ77eS
           result = success
       
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊👉 return = V4WtDJeJExC68HxdpQ77eS
       
 debug 
       «
        Julius creates 'new zealand spinach' because he/she uses 'new zealand spinach' in his/her cooking.
       »
       
 info 
       ╭┈◜POST◝┈┈ 🟢 ┈┈( recipes/post/ingredient-post/id )┈┈
       ┊                ┈┈>( traits/post-response )┈┈┈┈┈┈
       ┊ 🕒 105ms
       ┊ 🔑 Bearer
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊🗣️  Request
       ┊ = 
         method = POST
         url = http://localhost:7777/api/v1/ingredient
         
         🔝 headers
          = 
           [0] = Content-Type: application/json
           [1] = authorization: Bearer eyJhbGciOiJIUzUxMiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6IlRfSG9sZGVySjkxIiwibGFzdE5hbWUiOiJIb2xkZXItVGVzdGVyIiwiZmlyc3ROYW1lIjoiSnVsaXVzIiwicm9sZXMiOltdLCJpYXQiOjE3MTUzMjk3MzEsImV4cCI6MTcxNTkzNDUzMX0.sFb5ghCoscjnGZP7A11mTvF518pFa09f8ZCObulKZGjBFqcLiMhP9ywnvpRQ98kTrwuRlhnYmSWx75ofFsGO8w
         
         📃 body
          = 
           name = new zealand spinach
           cost = 60
           cost_currency = EUR
           quantity = 1000
           unit = g
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊🪃  Response
       ┊ = 
         statusCode = 201
         
         🔝 headers
          = 
           [0] = date: Fri, 10 May 2024 08:29:36 GMT
           [1] = request-id: 22220@LAPTOP-7D28KH4S/4ed5a4cac14854af5405f2bb-0000000000000008
           [2] = content-security-policy: report-uri http://localhost:7777/cspreport/send?time=1715329776000;
           [3] = cross-origin-embedder-policy: same-origin
           [4] = cross-origin-opener-policy: same-origin
           [5] = cross-origin-resource-policy: same-site
           [6] = x-dns-prefetch-control: off
           [7] = expect-ct: max-age=0
           [8] = x-frame-options: SAMEORIGIN
           [9] = strict-transport-security: max-age=15552000; includeSubDomains
           [10] = x-download-options: noopen
           [11] = x-content-type-options: nosniff
           [12] = origin-agent-cluster: ?1
           [13] = x-permitted-cross-domain-policies: none
           [14] = referrer-policy: strict-origin-when-cross-origin
           [15] = x-xss-protection: 0
           [16] = access-control-allow-origin: *
           [17] = access-control-allow-methods: GET,PUT,POST,DELETE,OPTIONS
           [18] = access-control-allow-headers: Origin, X-Requested-With, Content-Type, Accept
           [19] = sec-fetch-dest: image
           [20] = sec-fetch-mode: no-cors
           [21] = sec-fetch-site: cross-site
           [22] = content-type: application/json; charset=utf-8
           [23] = content-length: 178
           [24] = etag: W/"b2-ohyWng8bqBddNICvsbX/HJmvbAo"
           [25] = connection: close
         
         📃 body
          = 
           requestId = 22220@LAPTOP-7D28KH4S/4ed5a4cac14854af5405f2bb-0000000000000008
           id = 9uEvLhtg1nXQ3HHyMsXSAJ
           url = /api/v1/ingredient/9uEvLhtg1nXQ3HHyMsXSAJ
           result = success
       
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊👉 return = 9uEvLhtg1nXQ3HHyMsXSAJ
       
 debug 
       «
        Julius creates 'Rabbit' because he/she uses 'Rabbit' in his/her cooking.
       »
       
 info 
       ╭┈◜POST◝┈┈ 🟢 ┈┈( recipes/post/ingredient-post/id )┈┈
       ┊                ┈┈>( traits/post-response )┈┈┈┈┈┈
       ┊ 🕒 97ms
       ┊ 🔑 Bearer
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊🗣️  Request
       ┊ = 
         method = POST
         url = http://localhost:7777/api/v1/ingredient
         
         🔝 headers
          = 
           [0] = Content-Type: application/json
           [1] = authorization: Bearer eyJhbGciOiJIUzUxMiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6IlRfSG9sZGVySjkxIiwibGFzdE5hbWUiOiJIb2xkZXItVGVzdGVyIiwiZmlyc3ROYW1lIjoiSnVsaXVzIiwicm9sZXMiOltdLCJpYXQiOjE3MTUzMjk3MzEsImV4cCI6MTcxNTkzNDUzMX0.sFb5ghCoscjnGZP7A11mTvF518pFa09f8ZCObulKZGjBFqcLiMhP9ywnvpRQ98kTrwuRlhnYmSWx75ofFsGO8w
         
         📃 body
          = 
           name = Rabbit
           cost = 60
           cost_currency = EUR
           quantity = 1000
           unit = g
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊🪃  Response
       ┊ = 
         statusCode = 201
         
         🔝 headers
          = 
           [0] = date: Fri, 10 May 2024 08:29:36 GMT
           [1] = request-id: 22220@LAPTOP-7D28KH4S/4ed5a4cac14854af5405f2bb-0000000000000009
           [2] = content-security-policy: report-uri http://localhost:7777/cspreport/send?time=1715329776000;
           [3] = cross-origin-embedder-policy: same-origin
           [4] = cross-origin-opener-policy: same-origin
           [5] = cross-origin-resource-policy: same-site
           [6] = x-dns-prefetch-control: off
           [7] = expect-ct: max-age=0
           [8] = x-frame-options: SAMEORIGIN
           [9] = strict-transport-security: max-age=15552000; includeSubDomains
           [10] = x-download-options: noopen
           [11] = x-content-type-options: nosniff
           [12] = origin-agent-cluster: ?1
           [13] = x-permitted-cross-domain-policies: none
           [14] = referrer-policy: strict-origin-when-cross-origin
           [15] = x-xss-protection: 0
           [16] = access-control-allow-origin: *
           [17] = access-control-allow-methods: GET,PUT,POST,DELETE,OPTIONS
           [18] = access-control-allow-headers: Origin, X-Requested-With, Content-Type, Accept
           [19] = sec-fetch-dest: image
           [20] = sec-fetch-mode: no-cors
           [21] = sec-fetch-site: cross-site
           [22] = content-type: application/json; charset=utf-8
           [23] = content-length: 178
           [24] = etag: W/"b2-Se0Oq2Cz6X6/37JBsLOuvaA0mHA"
           [25] = connection: close
         
         📃 body
          = 
           requestId = 22220@LAPTOP-7D28KH4S/4ed5a4cac14854af5405f2bb-0000000000000009
           id = 4jESTgz1yvH11zVvgNyotY
           url = /api/v1/ingredient/4jESTgz1yvH11zVvgNyotY
           result = success
       
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊👉 return = 4jESTgz1yvH11zVvgNyotY
       
 debug 
       «
        Julius creates 'black bean' because he/she uses 'black bean' in his/her cooking.
       »
       
 info 
       ╭┈◜POST◝┈┈ 🟢 ┈┈( recipes/post/ingredient-post/id )┈┈
       ┊                ┈┈>( traits/post-response )┈┈┈┈┈┈
       ┊ 🕒 115ms
       ┊ 🔑 Bearer
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊🗣️  Request
       ┊ = 
         method = POST
         url = http://localhost:7777/api/v1/ingredient
         
         🔝 headers
          = 
           [0] = Content-Type: application/json
           [1] = authorization: Bearer eyJhbGciOiJIUzUxMiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6IlRfSG9sZGVySjkxIiwibGFzdE5hbWUiOiJIb2xkZXItVGVzdGVyIiwiZmlyc3ROYW1lIjoiSnVsaXVzIiwicm9sZXMiOltdLCJpYXQiOjE3MTUzMjk3MzEsImV4cCI6MTcxNTkzNDUzMX0.sFb5ghCoscjnGZP7A11mTvF518pFa09f8ZCObulKZGjBFqcLiMhP9ywnvpRQ98kTrwuRlhnYmSWx75ofFsGO8w
         
         📃 body
          = 
           name = black bean
           cost = 60
           cost_currency = EUR
           quantity = 1000
           unit = g
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊🪃  Response
       ┊ = 
         statusCode = 201
         
         🔝 headers
          = 
           [0] = date: Fri, 10 May 2024 08:29:36 GMT
           [1] = request-id: 22220@LAPTOP-7D28KH4S/4ed5a4cac14854af5405f2bb-0000000000000010
           [2] = content-security-policy: report-uri http://localhost:7777/cspreport/send?time=1715329776000;
           [3] = cross-origin-embedder-policy: same-origin
           [4] = cross-origin-opener-policy: same-origin
           [5] = cross-origin-resource-policy: same-site
           [6] = x-dns-prefetch-control: off
           [7] = expect-ct: max-age=0
           [8] = x-frame-options: SAMEORIGIN
           [9] = strict-transport-security: max-age=15552000; includeSubDomains
           [10] = x-download-options: noopen
           [11] = x-content-type-options: nosniff
           [12] = origin-agent-cluster: ?1
           [13] = x-permitted-cross-domain-policies: none
           [14] = referrer-policy: strict-origin-when-cross-origin
           [15] = x-xss-protection: 0
           [16] = access-control-allow-origin: *
           [17] = access-control-allow-methods: GET,PUT,POST,DELETE,OPTIONS
           [18] = access-control-allow-headers: Origin, X-Requested-With, Content-Type, Accept
           [19] = sec-fetch-dest: image
           [20] = sec-fetch-mode: no-cors
           [21] = sec-fetch-site: cross-site
           [22] = content-type: application/json; charset=utf-8
           [23] = content-length: 178
           [24] = etag: W/"b2-qSvVNc/6rUs5OJRGmHqSDGLj80U"
           [25] = connection: close
         
         📃 body
          = 
           requestId = 22220@LAPTOP-7D28KH4S/4ed5a4cac14854af5405f2bb-0000000000000010
           id = QF5ARxi37DNSWE7qKJSYaU
           url = /api/v1/ingredient/QF5ARxi37DNSWE7qKJSYaU
           result = success
       
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊👉 return = QF5ARxi37DNSWE7qKJSYaU
       
 debug 
       «
        Julius creates 'shallot' because he/she uses 'shallot' in his/her cooking.
       »
       
 info 
       ╭┈◜POST◝┈┈ 🟢 ┈┈( recipes/post/ingredient-post/id )┈┈
       ┊                ┈┈>( traits/post-response )┈┈┈┈┈┈
       ┊ 🕒 269ms
       ┊ 🔑 Bearer
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊🗣️  Request
       ┊ = 
         method = POST
         url = http://localhost:7777/api/v1/ingredient
         
         🔝 headers
          = 
           [0] = Content-Type: application/json
           [1] = authorization: Bearer eyJhbGciOiJIUzUxMiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6IlRfSG9sZGVySjkxIiwibGFzdE5hbWUiOiJIb2xkZXItVGVzdGVyIiwiZmlyc3ROYW1lIjoiSnVsaXVzIiwicm9sZXMiOltdLCJpYXQiOjE3MTUzMjk3MzEsImV4cCI6MTcxNTkzNDUzMX0.sFb5ghCoscjnGZP7A11mTvF518pFa09f8ZCObulKZGjBFqcLiMhP9ywnvpRQ98kTrwuRlhnYmSWx75ofFsGO8w
         
         📃 body
          = 
           name = shallot
           cost = 60
           cost_currency = EUR
           quantity = 1000
           unit = g
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊🪃  Response
       ┊ = 
         statusCode = 201
         
         🔝 headers
          = 
           [0] = date: Fri, 10 May 2024 08:29:36 GMT
           [1] = request-id: 22220@LAPTOP-7D28KH4S/4ed5a4cac14854af5405f2bb-0000000000000011
           [2] = content-security-policy: report-uri http://localhost:7777/cspreport/send?time=1715329776000;
           [3] = cross-origin-embedder-policy: same-origin
           [4] = cross-origin-opener-policy: same-origin
           [5] = cross-origin-resource-policy: same-site
           [6] = x-dns-prefetch-control: off
           [7] = expect-ct: max-age=0
           [8] = x-frame-options: SAMEORIGIN
           [9] = strict-transport-security: max-age=15552000; includeSubDomains
           [10] = x-download-options: noopen
           [11] = x-content-type-options: nosniff
           [12] = origin-agent-cluster: ?1
           [13] = x-permitted-cross-domain-policies: none
           [14] = referrer-policy: strict-origin-when-cross-origin
           [15] = x-xss-protection: 0
           [16] = access-control-allow-origin: *
           [17] = access-control-allow-methods: GET,PUT,POST,DELETE,OPTIONS
           [18] = access-control-allow-headers: Origin, X-Requested-With, Content-Type, Accept
           [19] = sec-fetch-dest: image
           [20] = sec-fetch-mode: no-cors
           [21] = sec-fetch-site: cross-site
           [22] = content-type: application/json; charset=utf-8
           [23] = content-length: 178
           [24] = etag: W/"b2-KfT/6eamJ5mpDy9cEGM20TzHcGo"
           [25] = connection: close
         
         📃 body
          = 
           requestId = 22220@LAPTOP-7D28KH4S/4ed5a4cac14854af5405f2bb-0000000000000011
           id = WUiCDyaCMCupLiLjWpzXB5
           url = /api/v1/ingredient/WUiCDyaCMCupLiLjWpzXB5
           result = success
       
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊👉 return = WUiCDyaCMCupLiLjWpzXB5
       
 debug 
       «
        Julius has 2 fabulous recipes
       and wish to share them on Bento Solidaires.
       »
       
 debug 
       «
        Julius creates recipe number#1
         'My super Nursehound with calabrese and new zealand spinach'
       »
       
 info 
       ╭┈◜POST◝┈┈ 🟢 ┈┈( recipes/post/recipe-post/id )┈┈
       ┊                ┈┈>( traits/post-response )┈┈┈┈┈┈
       ┊ 🕒 171ms
       ┊ 🔑 Bearer
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊🗣️  Request
       ┊ = 
         method = POST
         url = http://localhost:7777/api/v1/recipe
         
         🔝 headers
          = 
           [0] = Content-Type: application/json
           [1] = authorization: Bearer eyJhbGciOiJIUzUxMiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6IlRfSG9sZGVySjkxIiwibGFzdE5hbWUiOiJIb2xkZXItVGVzdGVyIiwiZmlyc3ROYW1lIjoiSnVsaXVzIiwicm9sZXMiOltdLCJpYXQiOjE3MTUzMjk3MzEsImV4cCI6MTcxNTkzNDUzMX0.sFb5ghCoscjnGZP7A11mTvF518pFa09f8ZCObulKZGjBFqcLiMhP9ywnvpRQ98kTrwuRlhnYmSWx75ofFsGO8w
         
         📃 body
          = 
           name = My super Nursehound with calabrese and new zealand spinach
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊🪃  Response
       ┊ = 
         statusCode = 201
         
         🔝 headers
          = 
           [0] = date: Fri, 10 May 2024 08:29:36 GMT
           [1] = request-id: 22220@LAPTOP-7D28KH4S/4ed5a4cac14854af5405f2bb-0000000000000012
           [2] = content-security-policy: report-uri http://localhost:7777/cspreport/send?time=1715329776000;
           [3] = cross-origin-embedder-policy: same-origin
           [4] = cross-origin-opener-policy: same-origin
           [5] = cross-origin-resource-policy: same-site
           [6] = x-dns-prefetch-control: off
           [7] = expect-ct: max-age=0
           [8] = x-frame-options: SAMEORIGIN
           [9] = strict-transport-security: max-age=15552000; includeSubDomains
           [10] = x-download-options: noopen
           [11] = x-content-type-options: nosniff
           [12] = origin-agent-cluster: ?1
           [13] = x-permitted-cross-domain-policies: none
           [14] = referrer-policy: strict-origin-when-cross-origin
           [15] = x-xss-protection: 0
           [16] = access-control-allow-origin: *
           [17] = access-control-allow-methods: GET,PUT,POST,DELETE,OPTIONS
           [18] = access-control-allow-headers: Origin, X-Requested-With, Content-Type, Accept
           [19] = sec-fetch-dest: image
           [20] = sec-fetch-mode: no-cors
           [21] = sec-fetch-site: cross-site
           [22] = content-type: application/json; charset=utf-8
           [23] = content-length: 174
           [24] = etag: W/"ae-dwIiLiL8dWSHpeodMc5gXtSRlX4"
           [25] = connection: close
         
         📃 body
          = 
           requestId = 22220@LAPTOP-7D28KH4S/4ed5a4cac14854af5405f2bb-0000000000000012
           id = VHnHwPWUYBortCCd7dXfb1
           url = /api/v1/recipe/VHnHwPWUYBortCCd7dXfb1
           result = success
       
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊👉 return = VHnHwPWUYBortCCd7dXfb1
       
 debug 
       «
        Julius's recipe number#1 is 'My super Nursehound with calabrese and new zealand spinach'
       Preparation is so simple:
       in one step, you put all 3 ingredients in the oven
       and wait for an hour at 150°C
       »
       
 debug 
       «
        Julius creates recipe 'My super Nursehound with calabrese and new zealand spinach' step 1.
       »
       
 debug 
       «
        Julius add each ingredient to 'My super Nursehound with calabrese and new zealand spinach' step 1.
       »
       
 info 
       ╭┈◜POST◝┈┈ 🟢 ┈┈( recipes/post/step-post/id )┈┈
       ┊                ┈┈>( traits/post-response )┈┈┈┈┈┈
       ┊ 🕒 147ms
       ┊ 🔑 Bearer
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊🗣️  Request
       ┊ = 
         method = POST
         url = http://localhost:7777/api/v1/recipe/VHnHwPWUYBortCCd7dXfb1/step
         
         🔝 headers
          = 
           [0] = Content-Type: application/json
           [1] = authorization: Bearer eyJhbGciOiJIUzUxMiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6IlRfSG9sZGVySjkxIiwibGFzdE5hbWUiOiJIb2xkZXItVGVzdGVyIiwiZmlyc3ROYW1lIjoiSnVsaXVzIiwicm9sZXMiOltdLCJpYXQiOjE3MTUzMjk3MzEsImV4cCI6MTcxNTkzNDUzMX0.sFb5ghCoscjnGZP7A11mTvF518pFa09f8ZCObulKZGjBFqcLiMhP9ywnvpRQ98kTrwuRlhnYmSWx75ofFsGO8w
         
         📃 body
          = 
           step = 0
           ingredients = 
             ► ingredientId = MfZR5wDt5Bcy3p9P43yAgY
               quantity = 250
               unit = g
             ► ingredientId = V4WtDJeJExC68HxdpQ77eS
               quantity = 250
               unit = g
             ► ingredientId = 9uEvLhtg1nXQ3HHyMsXSAJ
               quantity = 250
               unit = g
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊🪃  Response
       ┊ = 
         statusCode = 201
         
         🔝 headers
          = 
           [0] = date: Fri, 10 May 2024 08:29:36 GMT
           [1] = request-id: 22220@LAPTOP-7D28KH4S/4ed5a4cac14854af5405f2bb-0000000000000013
           [2] = content-security-policy: report-uri http://localhost:7777/cspreport/send?time=1715329776000;
           [3] = cross-origin-embedder-policy: same-origin
           [4] = cross-origin-opener-policy: same-origin
           [5] = cross-origin-resource-policy: same-site
           [6] = x-dns-prefetch-control: off
           [7] = expect-ct: max-age=0
           [8] = x-frame-options: SAMEORIGIN
           [9] = strict-transport-security: max-age=15552000; includeSubDomains
           [10] = x-download-options: noopen
           [11] = x-content-type-options: nosniff
           [12] = origin-agent-cluster: ?1
           [13] = x-permitted-cross-domain-policies: none
           [14] = referrer-policy: strict-origin-when-cross-origin
           [15] = x-xss-protection: 0
           [16] = access-control-allow-origin: *
           [17] = access-control-allow-methods: GET,PUT,POST,DELETE,OPTIONS
           [18] = access-control-allow-headers: Origin, X-Requested-With, Content-Type, Accept
           [19] = sec-fetch-dest: image
           [20] = sec-fetch-mode: no-cors
           [21] = sec-fetch-site: cross-site
           [22] = content-type: application/json; charset=utf-8
           [23] = content-length: 202
           [24] = etag: W/"ca-Ki44ZZZIxA1V41errOmNPVB6o9A"
           [25] = connection: close
         
         📃 body
          = 
           requestId = 22220@LAPTOP-7D28KH4S/4ed5a4cac14854af5405f2bb-0000000000000013
           id = 8grmaLrTpGxsKpqW4AKwBg
           url = /api/v1/recipe/VHnHwPWUYBortCCd7dXfb1/step/8grmaLrTpGxsKpqW4AKwBg
           result = success
       
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊👉 return = 8grmaLrTpGxsKpqW4AKwBg
       
 debug 
       «
        Julius creates recipe number#2
         'My spectacular Rabbit with black bean and shallot'
       »
       
 info 
       ╭┈◜POST◝┈┈ 🟢 ┈┈( recipes/post/recipe-post/id )┈┈
       ┊                ┈┈>( traits/post-response )┈┈┈┈┈┈
       ┊ 🕒 103ms
       ┊ 🔑 Bearer
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊🗣️  Request
       ┊ = 
         method = POST
         url = http://localhost:7777/api/v1/recipe
         
         🔝 headers
          = 
           [0] = Content-Type: application/json
           [1] = authorization: Bearer eyJhbGciOiJIUzUxMiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6IlRfSG9sZGVySjkxIiwibGFzdE5hbWUiOiJIb2xkZXItVGVzdGVyIiwiZmlyc3ROYW1lIjoiSnVsaXVzIiwicm9sZXMiOltdLCJpYXQiOjE3MTUzMjk3MzEsImV4cCI6MTcxNTkzNDUzMX0.sFb5ghCoscjnGZP7A11mTvF518pFa09f8ZCObulKZGjBFqcLiMhP9ywnvpRQ98kTrwuRlhnYmSWx75ofFsGO8w
         
         📃 body
          = 
           name = My spectacular Rabbit with black bean and shallot
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊🪃  Response
       ┊ = 
         statusCode = 201
         
         🔝 headers
          = 
           [0] = date: Fri, 10 May 2024 08:29:36 GMT
           [1] = request-id: 22220@LAPTOP-7D28KH4S/4ed5a4cac14854af5405f2bb-0000000000000014
           [2] = content-security-policy: report-uri http://localhost:7777/cspreport/send?time=1715329776000;
           [3] = cross-origin-embedder-policy: same-origin
           [4] = cross-origin-opener-policy: same-origin
           [5] = cross-origin-resource-policy: same-site
           [6] = x-dns-prefetch-control: off
           [7] = expect-ct: max-age=0
           [8] = x-frame-options: SAMEORIGIN
           [9] = strict-transport-security: max-age=15552000; includeSubDomains
           [10] = x-download-options: noopen
           [11] = x-content-type-options: nosniff
           [12] = origin-agent-cluster: ?1
           [13] = x-permitted-cross-domain-policies: none
           [14] = referrer-policy: strict-origin-when-cross-origin
           [15] = x-xss-protection: 0
           [16] = access-control-allow-origin: *
           [17] = access-control-allow-methods: GET,PUT,POST,DELETE,OPTIONS
           [18] = access-control-allow-headers: Origin, X-Requested-With, Content-Type, Accept
           [19] = sec-fetch-dest: image
           [20] = sec-fetch-mode: no-cors
           [21] = sec-fetch-site: cross-site
           [22] = content-type: application/json; charset=utf-8
           [23] = content-length: 174
           [24] = etag: W/"ae-3vEMov57j1z/6upmhJE45znWUFA"
           [25] = connection: close
         
         📃 body
          = 
           requestId = 22220@LAPTOP-7D28KH4S/4ed5a4cac14854af5405f2bb-0000000000000014
           id = 43uaEkxAJ2pDjQn87JE1Jc
           url = /api/v1/recipe/43uaEkxAJ2pDjQn87JE1Jc
           result = success
       
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊👉 return = 43uaEkxAJ2pDjQn87JE1Jc
       
 debug 
       «
        Julius's recipe number#2 is 'My spectacular Rabbit with black bean and shallot'
       Preparation is so simple:
       in one step, you put all 3 ingredients in the oven
       and wait for an hour at 150°C
       »
       
 debug 
       «
        Julius creates recipe 'My spectacular Rabbit with black bean and shallot' step 1.
       »
       
 debug 
       «
        Julius add each ingredient to 'My spectacular Rabbit with black bean and shallot' step 1.
       »
       
 info 
       ╭┈◜POST◝┈┈ 🟢 ┈┈( recipes/post/step-post/id )┈┈
       ┊                ┈┈>( traits/post-response )┈┈┈┈┈┈
       ┊ 🕒 198ms
       ┊ 🔑 Bearer
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊🗣️  Request
       ┊ = 
         method = POST
         url = http://localhost:7777/api/v1/recipe/43uaEkxAJ2pDjQn87JE1Jc/step
         
         🔝 headers
          = 
           [0] = Content-Type: application/json
           [1] = authorization: Bearer eyJhbGciOiJIUzUxMiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6IlRfSG9sZGVySjkxIiwibGFzdE5hbWUiOiJIb2xkZXItVGVzdGVyIiwiZmlyc3ROYW1lIjoiSnVsaXVzIiwicm9sZXMiOltdLCJpYXQiOjE3MTUzMjk3MzEsImV4cCI6MTcxNTkzNDUzMX0.sFb5ghCoscjnGZP7A11mTvF518pFa09f8ZCObulKZGjBFqcLiMhP9ywnvpRQ98kTrwuRlhnYmSWx75ofFsGO8w
         
         📃 body
          = 
           step = 0
           ingredients = 
             ► ingredientId = 4jESTgz1yvH11zVvgNyotY
               quantity = 250
               unit = g
             ► ingredientId = QF5ARxi37DNSWE7qKJSYaU
               quantity = 250
               unit = g
             ► ingredientId = WUiCDyaCMCupLiLjWpzXB5
               quantity = 250
               unit = g
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊🪃  Response
       ┊ = 
         statusCode = 201
         
         🔝 headers
          = 
           [0] = date: Fri, 10 May 2024 08:29:36 GMT
           [1] = request-id: 22220@LAPTOP-7D28KH4S/4ed5a4cac14854af5405f2bb-0000000000000015
           [2] = content-security-policy: report-uri http://localhost:7777/cspreport/send?time=1715329776000;
           [3] = cross-origin-embedder-policy: same-origin
           [4] = cross-origin-opener-policy: same-origin
           [5] = cross-origin-resource-policy: same-site
           [6] = x-dns-prefetch-control: off
           [7] = expect-ct: max-age=0
           [8] = x-frame-options: SAMEORIGIN
           [9] = strict-transport-security: max-age=15552000; includeSubDomains
           [10] = x-download-options: noopen
           [11] = x-content-type-options: nosniff
           [12] = origin-agent-cluster: ?1
           [13] = x-permitted-cross-domain-policies: none
           [14] = referrer-policy: strict-origin-when-cross-origin
           [15] = x-xss-protection: 0
           [16] = access-control-allow-origin: *
           [17] = access-control-allow-methods: GET,PUT,POST,DELETE,OPTIONS
           [18] = access-control-allow-headers: Origin, X-Requested-With, Content-Type, Accept
           [19] = sec-fetch-dest: image
           [20] = sec-fetch-mode: no-cors
           [21] = sec-fetch-site: cross-site
           [22] = content-type: application/json; charset=utf-8
           [23] = content-length: 202
           [24] = etag: W/"ca-DykCTHqHaCeBDjIvVjbb+/DHJ4s"
           [25] = connection: close
         
         📃 body
          = 
           requestId = 22220@LAPTOP-7D28KH4S/4ed5a4cac14854af5405f2bb-0000000000000015
           id = AsTqe1XoxRa2DdKJBfqkXu
           url = /api/v1/recipe/43uaEkxAJ2pDjQn87JE1Jc/step/AsTqe1XoxRa2DdKJBfqkXu
           result = success
       
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊👉 return = AsTqe1XoxRa2DdKJBfqkXu
       
 debug 
       «
        Julius propose to cook 1 bento
       every day for 4 days
       »
       
 debug 
       «
        🕒 rev.2
       >Server says time is  Fri, 10 May 2024 09:28:51 GMT<
        Local  says time is  Fri, 10 May 2024 08:28:57 GMT
        expect/actual jitter +3595ms / +3594ms  delta +1ms
       »
       
 debug   PROPOSITION
       ┈┈┈┈┈┈┈┈┈┈┈┈┈
       «
        Julius propose to cook 'My super Nursehound with calabrese and new zealand spinach' at Fri May 10 2024 11:28:56 GMT+0200 (Central European Summer Time)
       »
       
 info 
       ╭┈◜POST◝┈┈ 🟢 ┈┈( propositions/cook/post/id )┈┈
       ┊                ┈┈>( traits/post-response )┈┈┈┈┈┈
       ┊ 🕒 124ms
       ┊ 🔑 T_HolderJ91
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊🗣️  Request
       ┊ = 
         method = POST
         url = http://localhost:7777/api/v1/cook/proposition
         
         🔝 headers
          = 
           [0] = Content-Type: application/json
           [1] = authorization: Bearer eyJhbGciOiJIUzUxMiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6IlRfSG9sZGVySjkxIiwibGFzdE5hbWUiOiJIb2xkZXItVGVzdGVyIiwiZmlyc3ROYW1lIjoiSnVsaXVzIiwicm9sZXMiOltdLCJpYXQiOjE3MTUzMzMzMzEsImV4cCI6MTcxNTkzODEzMX0.Pkg8aLkZH_ybNIw49LbUOskSDldYj4FhgeJ7jdqb5F32S2jvPitxf7hJ2AUmfhxD3IkJoGGVp385yrQcNxqTHg
         
         📃 body
          = 
           recipeId = VHnHwPWUYBortCCd7dXfb1
           cook_hour = 11
           cook_minute = 28
           cook_day = 0
           servings = 1
           expected = 
             role_swap = false
             box_return = true
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊🪃  Response
       ┊ = 
         statusCode = 201
         
         🔝 headers
          = 
           [0] = date: Fri, 10 May 2024 09:28:51 GMT
           [1] = request-id: 22220@LAPTOP-7D28KH4S/4ed5a4cac14854af5405f2bb-0000000000000019
           [2] = content-security-policy: report-uri http://localhost:7777/cspreport/send?time=1715333331000;
           [3] = cross-origin-embedder-policy: same-origin
           [4] = cross-origin-opener-policy: same-origin
           [5] = cross-origin-resource-policy: same-site
           [6] = x-dns-prefetch-control: off
           [7] = expect-ct: max-age=0
           [8] = x-frame-options: SAMEORIGIN
           [9] = strict-transport-security: max-age=15552000; includeSubDomains
           [10] = x-download-options: noopen
           [11] = x-content-type-options: nosniff
           [12] = origin-agent-cluster: ?1
           [13] = x-permitted-cross-domain-policies: none
           [14] = referrer-policy: strict-origin-when-cross-origin
           [15] = x-xss-protection: 0
           [16] = access-control-allow-origin: *
           [17] = access-control-allow-methods: GET,PUT,POST,DELETE,OPTIONS
           [18] = access-control-allow-headers: Origin, X-Requested-With, Content-Type, Accept
           [19] = sec-fetch-dest: image
           [20] = sec-fetch-mode: no-cors
           [21] = sec-fetch-site: cross-site
           [22] = content-type: application/json; charset=utf-8
           [23] = content-length: 225
           [24] = etag: W/"e1-61D/OFGXHAp1dFCxD0rSAWig9Rw"
           [25] = connection: close
         
         📃 body
          = 
           requestId = 22220@LAPTOP-7D28KH4S/4ed5a4cac14854af5405f2bb-0000000000000019
           id = 9cU3JXa5Ujf7e4EgdwDGbC
           url = /api/v1/cook/proposition/9cU3JXa5Ujf7e4EgdwDGbC
           validToDate = 2024-05-12T09:28:00.000Z
           result = success
       
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊👉 return = 9cU3JXa5Ujf7e4EgdwDGbC
       
 debug 
       «
        Julius offers one bento for delivery at Fri May 10 2024 11:28:56 GMT+0200 (Central European Summer Time) at 'the nice place'
       »
       
 info 
       ╭┈◜POST◝┈┈ 🟢 ┈┈( propositions/meetings/cook/post/id )┈┈
       ┊                ┈┈>( traits/post-response )┈┈┈┈┈┈
       ┊ 🕒 121ms
       ┊ 🔑 T_HolderJ91
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊🗣️  Request
       ┊ = 
         method = POST
         url = http://localhost:7777/api/v1/cook/meet
         
         🔝 headers
          = 
           [0] = Content-Type: application/json
           [1] = authorization: Bearer eyJhbGciOiJIUzUxMiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6IlRfSG9sZGVySjkxIiwibGFzdE5hbWUiOiJIb2xkZXItVGVzdGVyIiwiZmlyc3ROYW1lIjoiSnVsaXVzIiwicm9sZXMiOltdLCJpYXQiOjE3MTUzMzMzMzEsImV4cCI6MTcxNTkzODEzMX0.Pkg8aLkZH_ybNIw49LbUOskSDldYj4FhgeJ7jdqb5F32S2jvPitxf7hJ2AUmfhxD3IkJoGGVp385yrQcNxqTHg
         
         📃 body
          = 
           name = new meeting
           meetPlace = the nice place
           meetFromDate = 2024-05-10T09:28:56.965Z
           meetToDate = 2024-05-10T09:43:56.965Z
           meetCoordinates = 
             lat = 41
             lng = 12
           cookPropositionId = 9cU3JXa5Ujf7e4EgdwDGbC
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊🪃  Response
       ┊ = 
         statusCode = 201
         
         🔝 headers
          = 
           [0] = date: Fri, 10 May 2024 09:28:51 GMT
           [1] = request-id: 22220@LAPTOP-7D28KH4S/4ed5a4cac14854af5405f2bb-0000000000000020
           [2] = content-security-policy: report-uri http://localhost:7777/cspreport/send?time=1715333331000;
           [3] = cross-origin-embedder-policy: same-origin
           [4] = cross-origin-opener-policy: same-origin
           [5] = cross-origin-resource-policy: same-site
           [6] = x-dns-prefetch-control: off
           [7] = expect-ct: max-age=0
           [8] = x-frame-options: SAMEORIGIN
           [9] = strict-transport-security: max-age=15552000; includeSubDomains
           [10] = x-download-options: noopen
           [11] = x-content-type-options: nosniff
           [12] = origin-agent-cluster: ?1
           [13] = x-permitted-cross-domain-policies: none
           [14] = referrer-policy: strict-origin-when-cross-origin
           [15] = x-xss-protection: 0
           [16] = access-control-allow-origin: *
           [17] = access-control-allow-methods: GET,PUT,POST,DELETE,OPTIONS
           [18] = access-control-allow-headers: Origin, X-Requested-With, Content-Type, Accept
           [19] = sec-fetch-dest: image
           [20] = sec-fetch-mode: no-cors
           [21] = sec-fetch-site: cross-site
           [22] = content-type: application/json; charset=utf-8
           [23] = content-length: 177
           [24] = etag: W/"b1-ha5QPLIOazZq5KOcdu1qodUK0dE"
           [25] = connection: close
         
         📃 body
          = 
           requestId = 22220@LAPTOP-7D28KH4S/4ed5a4cac14854af5405f2bb-0000000000000020
           id = lnv76fz9fqgWztgwbYJep4
           url = /api/v1/cook/meet/lnv76fz9fqgWztgwbYJep4
           result = success
       
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊👉 return = lnv76fz9fqgWztgwbYJep4
       
 debug 
       «
        as an alternative Julius offers delivery at Fri May 10 2024 11:28:56 GMT+0200 (Central European Summer Time) at 'the nice place'
       »
       
 info 
       ╭┈◜POST◝┈┈ 🟢 ┈┈( propositions/meetings/cook/post/id )┈┈
       ┊                ┈┈>( traits/post-response )┈┈┈┈┈┈
       ┊ 🕒 158ms
       ┊ 🔑 T_HolderJ91
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊🗣️  Request
       ┊ = 
         method = POST
         url = http://localhost:7777/api/v1/cook/meet
         
         🔝 headers
          = 
           [0] = Content-Type: application/json
           [1] = authorization: Bearer eyJhbGciOiJIUzUxMiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6IlRfSG9sZGVySjkxIiwibGFzdE5hbWUiOiJIb2xkZXItVGVzdGVyIiwiZmlyc3ROYW1lIjoiSnVsaXVzIiwicm9sZXMiOltdLCJpYXQiOjE3MTUzMzMzMzEsImV4cCI6MTcxNTkzODEzMX0.Pkg8aLkZH_ybNIw49LbUOskSDldYj4FhgeJ7jdqb5F32S2jvPitxf7hJ2AUmfhxD3IkJoGGVp385yrQcNxqTHg
         
         📃 body
          = 
           name = new meeting
           meetPlace = the nice place
           meetFromDate = 2024-05-10T09:28:56.965Z
           meetToDate = 2024-05-10T09:43:56.965Z
           meetCoordinates = 
             lat = 41
             lng = 12
           cookPropositionId = 9cU3JXa5Ujf7e4EgdwDGbC
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊🪃  Response
       ┊ = 
         statusCode = 201
         
         🔝 headers
          = 
           [0] = date: Fri, 10 May 2024 09:28:51 GMT
           [1] = request-id: 22220@LAPTOP-7D28KH4S/4ed5a4cac14854af5405f2bb-0000000000000021
           [2] = content-security-policy: report-uri http://localhost:7777/cspreport/send?time=1715333331000;
           [3] = cross-origin-embedder-policy: same-origin
           [4] = cross-origin-opener-policy: same-origin
           [5] = cross-origin-resource-policy: same-site
           [6] = x-dns-prefetch-control: off
           [7] = expect-ct: max-age=0
           [8] = x-frame-options: SAMEORIGIN
           [9] = strict-transport-security: max-age=15552000; includeSubDomains
           [10] = x-download-options: noopen
           [11] = x-content-type-options: nosniff
           [12] = origin-agent-cluster: ?1
           [13] = x-permitted-cross-domain-policies: none
           [14] = referrer-policy: strict-origin-when-cross-origin
           [15] = x-xss-protection: 0
           [16] = access-control-allow-origin: *
           [17] = access-control-allow-methods: GET,PUT,POST,DELETE,OPTIONS
           [18] = access-control-allow-headers: Origin, X-Requested-With, Content-Type, Accept
           [19] = sec-fetch-dest: image
           [20] = sec-fetch-mode: no-cors
           [21] = sec-fetch-site: cross-site
           [22] = content-type: application/json; charset=utf-8
           [23] = content-length: 177
           [24] = etag: W/"b1-dw4yA/5OEsJ/2SbvR8pjEKIiiwg"
           [25] = connection: close
         
         📃 body
          = 
           requestId = 22220@LAPTOP-7D28KH4S/4ed5a4cac14854af5405f2bb-0000000000000021
           id = lFids5y62g2YjcWVavLgs9
           url = /api/v1/cook/meet/lFids5y62g2YjcWVavLgs9
           result = success
       
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊👉 return = lFids5y62g2YjcWVavLgs9
       
 debug 
       «
        🕒 rev.3
       >Server says time is  Sat, 11 May 2024 09:28:51 GMT<
        Local  says time is  Fri, 10 May 2024 08:28:57 GMT
        expect/actual jitter +89994ms / +89993ms  delta +1ms
       »
       
 debug   PROPOSITION
       ┈┈┈┈┈┈┈┈┈┈┈┈┈
       «
        Julius propose to cook 'My spectacular Rabbit with black bean and shallot' at Sat May 11 2024 11:28:56 GMT+0200 (Central European Summer Time)
       »
       
 info 
       ╭┈◜POST◝┈┈ 🟢 ┈┈( propositions/cook/post/id )┈┈
       ┊                ┈┈>( traits/post-response )┈┈┈┈┈┈
       ┊ 🕒 202ms
       ┊ 🔑 T_HolderJ91
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊🗣️  Request
       ┊ = 
         method = POST
         url = http://localhost:7777/api/v1/cook/proposition
         
         🔝 headers
          = 
           [0] = Content-Type: application/json
           [1] = authorization: Bearer eyJhbGciOiJIUzUxMiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6IlRfSG9sZGVySjkxIiwibGFzdE5hbWUiOiJIb2xkZXItVGVzdGVyIiwiZmlyc3ROYW1lIjoiSnVsaXVzIiwicm9sZXMiOltdLCJpYXQiOjE3MTU0MTk3MzEsImV4cCI6MTcxNjAyNDUzMX0.xUqFrXwqDK9Z3y6XEIYwi-C6ezHUQU7gojiXWkoaCXQM1Z1rQZYSwRSGNVOdHGA46vwlphqvVFZaHDkKSDnOUw
         
         📃 body
          = 
           recipeId = 43uaEkxAJ2pDjQn87JE1Jc
           cook_hour = 11
           cook_minute = 28
           cook_day = 0
           servings = 1
           expected = 
             role_swap = false
             box_return = true
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊🪃  Response
       ┊ = 
         statusCode = 201
         
         🔝 headers
          = 
           [0] = date: Sat, 11 May 2024 09:28:51 GMT
           [1] = request-id: 22220@LAPTOP-7D28KH4S/4ed5a4cac14854af5405f2bb-0000000000000025
           [2] = content-security-policy: report-uri http://localhost:7777/cspreport/send?time=1715419731000;
           [3] = cross-origin-embedder-policy: same-origin
           [4] = cross-origin-opener-policy: same-origin
           [5] = cross-origin-resource-policy: same-site
           [6] = x-dns-prefetch-control: off
           [7] = expect-ct: max-age=0
           [8] = x-frame-options: SAMEORIGIN
           [9] = strict-transport-security: max-age=15552000; includeSubDomains
           [10] = x-download-options: noopen
           [11] = x-content-type-options: nosniff
           [12] = origin-agent-cluster: ?1
           [13] = x-permitted-cross-domain-policies: none
           [14] = referrer-policy: strict-origin-when-cross-origin
           [15] = x-xss-protection: 0
           [16] = access-control-allow-origin: *
           [17] = access-control-allow-methods: GET,PUT,POST,DELETE,OPTIONS
           [18] = access-control-allow-headers: Origin, X-Requested-With, Content-Type, Accept
           [19] = sec-fetch-dest: image
           [20] = sec-fetch-mode: no-cors
           [21] = sec-fetch-site: cross-site
           [22] = content-type: application/json; charset=utf-8
           [23] = content-length: 225
           [24] = etag: W/"e1-HfN8QY30xTuLto44tVMSXAQK7AI"
           [25] = connection: close
         
         📃 body
          = 
           requestId = 22220@LAPTOP-7D28KH4S/4ed5a4cac14854af5405f2bb-0000000000000025
           id = leMTMh3SbdcZ9U8dHwg1MN
           url = /api/v1/cook/proposition/leMTMh3SbdcZ9U8dHwg1MN
           validToDate = 2024-05-13T09:28:00.000Z
           result = success
       
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊👉 return = leMTMh3SbdcZ9U8dHwg1MN
       
 debug 
       «
        Julius offers one bento for delivery at Sat May 11 2024 11:28:56 GMT+0200 (Central European Summer Time) at 'the nice place'
       »
       
 info 
       ╭┈◜POST◝┈┈ 🟢 ┈┈( propositions/meetings/cook/post/id )┈┈
       ┊                ┈┈>( traits/post-response )┈┈┈┈┈┈
       ┊ 🕒 139ms
       ┊ 🔑 T_HolderJ91
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊🗣️  Request
       ┊ = 
         method = POST
         url = http://localhost:7777/api/v1/cook/meet
         
         🔝 headers
          = 
           [0] = Content-Type: application/json
           [1] = authorization: Bearer eyJhbGciOiJIUzUxMiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6IlRfSG9sZGVySjkxIiwibGFzdE5hbWUiOiJIb2xkZXItVGVzdGVyIiwiZmlyc3ROYW1lIjoiSnVsaXVzIiwicm9sZXMiOltdLCJpYXQiOjE3MTU0MTk3MzEsImV4cCI6MTcxNjAyNDUzMX0.xUqFrXwqDK9Z3y6XEIYwi-C6ezHUQU7gojiXWkoaCXQM1Z1rQZYSwRSGNVOdHGA46vwlphqvVFZaHDkKSDnOUw
         
         📃 body
          = 
           name = new meeting
           meetPlace = the nice place
           meetFromDate = 2024-05-11T09:28:56.965Z
           meetToDate = 2024-05-11T09:43:56.965Z
           meetCoordinates = 
             lat = 41
             lng = 12
           cookPropositionId = leMTMh3SbdcZ9U8dHwg1MN
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊🪃  Response
       ┊ = 
         statusCode = 201
         
         🔝 headers
          = 
           [0] = date: Sat, 11 May 2024 09:28:51 GMT
           [1] = request-id: 22220@LAPTOP-7D28KH4S/4ed5a4cac14854af5405f2bb-0000000000000026
           [2] = content-security-policy: report-uri http://localhost:7777/cspreport/send?time=1715419731000;
           [3] = cross-origin-embedder-policy: same-origin
           [4] = cross-origin-opener-policy: same-origin
           [5] = cross-origin-resource-policy: same-site
           [6] = x-dns-prefetch-control: off
           [7] = expect-ct: max-age=0
           [8] = x-frame-options: SAMEORIGIN
           [9] = strict-transport-security: max-age=15552000; includeSubDomains
           [10] = x-download-options: noopen
           [11] = x-content-type-options: nosniff
           [12] = origin-agent-cluster: ?1
           [13] = x-permitted-cross-domain-policies: none
           [14] = referrer-policy: strict-origin-when-cross-origin
           [15] = x-xss-protection: 0
           [16] = access-control-allow-origin: *
           [17] = access-control-allow-methods: GET,PUT,POST,DELETE,OPTIONS
           [18] = access-control-allow-headers: Origin, X-Requested-With, Content-Type, Accept
           [19] = sec-fetch-dest: image
           [20] = sec-fetch-mode: no-cors
           [21] = sec-fetch-site: cross-site
           [22] = content-type: application/json; charset=utf-8
           [23] = content-length: 177
           [24] = etag: W/"b1-jDc6VWz2vscOthfNR6Y7yLfk1Kw"
           [25] = connection: close
         
         📃 body
          = 
           requestId = 22220@LAPTOP-7D28KH4S/4ed5a4cac14854af5405f2bb-0000000000000026
           id = QEvKMTED4Ey4kwgZCqzvoT
           url = /api/v1/cook/meet/QEvKMTED4Ey4kwgZCqzvoT
           result = success
       
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊👉 return = QEvKMTED4Ey4kwgZCqzvoT
       
 debug 
       «
        as an alternative Julius offers delivery at Sat May 11 2024 11:28:56 GMT+0200 (Central European Summer Time) at 'the nice place'
       »
       
 info 
       ╭┈◜POST◝┈┈ 🟢 ┈┈( propositions/meetings/cook/post/id )┈┈
       ┊                ┈┈>( traits/post-response )┈┈┈┈┈┈
       ┊ 🕒 201ms
       ┊ 🔑 T_HolderJ91
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊🗣️  Request
       ┊ = 
         method = POST
         url = http://localhost:7777/api/v1/cook/meet
         
         🔝 headers
          = 
           [0] = Content-Type: application/json
           [1] = authorization: Bearer eyJhbGciOiJIUzUxMiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6IlRfSG9sZGVySjkxIiwibGFzdE5hbWUiOiJIb2xkZXItVGVzdGVyIiwiZmlyc3ROYW1lIjoiSnVsaXVzIiwicm9sZXMiOltdLCJpYXQiOjE3MTU0MTk3MzEsImV4cCI6MTcxNjAyNDUzMX0.xUqFrXwqDK9Z3y6XEIYwi-C6ezHUQU7gojiXWkoaCXQM1Z1rQZYSwRSGNVOdHGA46vwlphqvVFZaHDkKSDnOUw
         
         📃 body
          = 
           name = new meeting
           meetPlace = the nice place
           meetFromDate = 2024-05-11T09:28:56.965Z
           meetToDate = 2024-05-11T09:43:56.965Z
           meetCoordinates = 
             lat = 41
             lng = 12
           cookPropositionId = leMTMh3SbdcZ9U8dHwg1MN
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊🪃  Response
       ┊ = 
         statusCode = 201
         
         🔝 headers
          = 
           [0] = date: Sat, 11 May 2024 09:28:51 GMT
           [1] = request-id: 22220@LAPTOP-7D28KH4S/4ed5a4cac14854af5405f2bb-0000000000000027
           [2] = content-security-policy: report-uri http://localhost:7777/cspreport/send?time=1715419731000;
           [3] = cross-origin-embedder-policy: same-origin
           [4] = cross-origin-opener-policy: same-origin
           [5] = cross-origin-resource-policy: same-site
           [6] = x-dns-prefetch-control: off
           [7] = expect-ct: max-age=0
           [8] = x-frame-options: SAMEORIGIN
           [9] = strict-transport-security: max-age=15552000; includeSubDomains
           [10] = x-download-options: noopen
           [11] = x-content-type-options: nosniff
           [12] = origin-agent-cluster: ?1
           [13] = x-permitted-cross-domain-policies: none
           [14] = referrer-policy: strict-origin-when-cross-origin
           [15] = x-xss-protection: 0
           [16] = access-control-allow-origin: *
           [17] = access-control-allow-methods: GET,PUT,POST,DELETE,OPTIONS
           [18] = access-control-allow-headers: Origin, X-Requested-With, Content-Type, Accept
           [19] = sec-fetch-dest: image
           [20] = sec-fetch-mode: no-cors
           [21] = sec-fetch-site: cross-site
           [22] = content-type: application/json; charset=utf-8
           [23] = content-length: 177
           [24] = etag: W/"b1-W5h14PZAxG3oHxpDOUMkCfQXOdQ"
           [25] = connection: close
         
         📃 body
          = 
           requestId = 22220@LAPTOP-7D28KH4S/4ed5a4cac14854af5405f2bb-0000000000000027
           id = Nv2ba2nD6Dehx6AUZGK1N6
           url = /api/v1/cook/meet/Nv2ba2nD6Dehx6AUZGK1N6
           result = success
       
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊👉 return = Nv2ba2nD6Dehx6AUZGK1N6
       
 debug 
       «
        🕒 rev.4
       >Server says time is  Sun, 12 May 2024 11:28:51 GMT<
        Local  says time is  Fri, 10 May 2024 08:28:58 GMT
        expect/actual jitter +183593ms / +183592ms  delta +1ms
       »
       
 debug   PROPOSITION
       ┈┈┈┈┈┈┈┈┈┈┈┈┈
       «
        Julius propose to cook 'My super Nursehound with calabrese and new zealand spinach' at Sun May 12 2024 13:28:56 GMT+0200 (Central European Summer Time)
       »
       
 info 
       ╭┈◜POST◝┈┈ 🟢 ┈┈( propositions/cook/post/id )┈┈
       ┊                ┈┈>( traits/post-response )┈┈┈┈┈┈
       ┊ 🕒 115ms
       ┊ 🔑 T_HolderJ91
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊🗣️  Request
       ┊ = 
         method = POST
         url = http://localhost:7777/api/v1/cook/proposition
         
         🔝 headers
          = 
           [0] = Content-Type: application/json
           [1] = authorization: Bearer eyJhbGciOiJIUzUxMiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6IlRfSG9sZGVySjkxIiwibGFzdE5hbWUiOiJIb2xkZXItVGVzdGVyIiwiZmlyc3ROYW1lIjoiSnVsaXVzIiwicm9sZXMiOltdLCJpYXQiOjE3MTU1MTMzMzEsImV4cCI6MTcxNjExODEzMX0.4oyqWll7acTU9sGiR6F94VOhINmYV0DifTyxvn0O-S14fhsZb-flrbytOgPsM75jz7A1ahGjrXIFRrpmNeR28w
         
         📃 body
          = 
           recipeId = VHnHwPWUYBortCCd7dXfb1
           cook_hour = 13
           cook_minute = 28
           cook_day = 0
           servings = 1
           expected = 
             role_swap = false
             box_return = true
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊🪃  Response
       ┊ = 
         statusCode = 201
         
         🔝 headers
          = 
           [0] = date: Sun, 12 May 2024 11:28:51 GMT
           [1] = request-id: 22220@LAPTOP-7D28KH4S/4ed5a4cac14854af5405f2bb-0000000000000031
           [2] = content-security-policy: report-uri http://localhost:7777/cspreport/send?time=1715513331000;
           [3] = cross-origin-embedder-policy: same-origin
           [4] = cross-origin-opener-policy: same-origin
           [5] = cross-origin-resource-policy: same-site
           [6] = x-dns-prefetch-control: off
           [7] = expect-ct: max-age=0
           [8] = x-frame-options: SAMEORIGIN
           [9] = strict-transport-security: max-age=15552000; includeSubDomains
           [10] = x-download-options: noopen
           [11] = x-content-type-options: nosniff
           [12] = origin-agent-cluster: ?1
           [13] = x-permitted-cross-domain-policies: none
           [14] = referrer-policy: strict-origin-when-cross-origin
           [15] = x-xss-protection: 0
           [16] = access-control-allow-origin: *
           [17] = access-control-allow-methods: GET,PUT,POST,DELETE,OPTIONS
           [18] = access-control-allow-headers: Origin, X-Requested-With, Content-Type, Accept
           [19] = sec-fetch-dest: image
           [20] = sec-fetch-mode: no-cors
           [21] = sec-fetch-site: cross-site
           [22] = content-type: application/json; charset=utf-8
           [23] = content-length: 225
           [24] = etag: W/"e1-y4AkUZBaJXvGJdbnK8Mii191QUQ"
           [25] = connection: close
         
         📃 body
          = 
           requestId = 22220@LAPTOP-7D28KH4S/4ed5a4cac14854af5405f2bb-0000000000000031
           id = JxsUWNxU4BjM6XUVMErehJ
           url = /api/v1/cook/proposition/JxsUWNxU4BjM6XUVMErehJ
           validToDate = 2024-05-14T11:28:00.000Z
           result = success
       
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊👉 return = JxsUWNxU4BjM6XUVMErehJ
       
 debug 
       «
        Julius offers one bento for delivery at Sun May 12 2024 13:28:56 GMT+0200 (Central European Summer Time) at 'the nice place'
       »
       
 info 
       ╭┈◜POST◝┈┈ 🟢 ┈┈( propositions/meetings/cook/post/id )┈┈
       ┊                ┈┈>( traits/post-response )┈┈┈┈┈┈
       ┊ 🕒 129ms
       ┊ 🔑 T_HolderJ91
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊🗣️  Request
       ┊ = 
         method = POST
         url = http://localhost:7777/api/v1/cook/meet
         
         🔝 headers
          = 
           [0] = Content-Type: application/json
           [1] = authorization: Bearer eyJhbGciOiJIUzUxMiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6IlRfSG9sZGVySjkxIiwibGFzdE5hbWUiOiJIb2xkZXItVGVzdGVyIiwiZmlyc3ROYW1lIjoiSnVsaXVzIiwicm9sZXMiOltdLCJpYXQiOjE3MTU1MTMzMzEsImV4cCI6MTcxNjExODEzMX0.4oyqWll7acTU9sGiR6F94VOhINmYV0DifTyxvn0O-S14fhsZb-flrbytOgPsM75jz7A1ahGjrXIFRrpmNeR28w
         
         📃 body
          = 
           name = new meeting
           meetPlace = the nice place
           meetFromDate = 2024-05-12T11:28:56.965Z
           meetToDate = 2024-05-12T11:43:56.965Z
           meetCoordinates = 
             lat = 41
             lng = 12
           cookPropositionId = JxsUWNxU4BjM6XUVMErehJ
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊🪃  Response
       ┊ = 
         statusCode = 201
         
         🔝 headers
          = 
           [0] = date: Sun, 12 May 2024 11:28:51 GMT
           [1] = request-id: 22220@LAPTOP-7D28KH4S/4ed5a4cac14854af5405f2bb-0000000000000032
           [2] = content-security-policy: report-uri http://localhost:7777/cspreport/send?time=1715513331000;
           [3] = cross-origin-embedder-policy: same-origin
           [4] = cross-origin-opener-policy: same-origin
           [5] = cross-origin-resource-policy: same-site
           [6] = x-dns-prefetch-control: off
           [7] = expect-ct: max-age=0
           [8] = x-frame-options: SAMEORIGIN
           [9] = strict-transport-security: max-age=15552000; includeSubDomains
           [10] = x-download-options: noopen
           [11] = x-content-type-options: nosniff
           [12] = origin-agent-cluster: ?1
           [13] = x-permitted-cross-domain-policies: none
           [14] = referrer-policy: strict-origin-when-cross-origin
           [15] = x-xss-protection: 0
           [16] = access-control-allow-origin: *
           [17] = access-control-allow-methods: GET,PUT,POST,DELETE,OPTIONS
           [18] = access-control-allow-headers: Origin, X-Requested-With, Content-Type, Accept
           [19] = sec-fetch-dest: image
           [20] = sec-fetch-mode: no-cors
           [21] = sec-fetch-site: cross-site
           [22] = content-type: application/json; charset=utf-8
           [23] = content-length: 177
           [24] = etag: W/"b1-6UJQ8w34hmcGURBzSfWNvYtT7og"
           [25] = connection: close
         
         📃 body
          = 
           requestId = 22220@LAPTOP-7D28KH4S/4ed5a4cac14854af5405f2bb-0000000000000032
           id = PPvLZvWA1kRzUYY7XHYdUz
           url = /api/v1/cook/meet/PPvLZvWA1kRzUYY7XHYdUz
           result = success
       
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊👉 return = PPvLZvWA1kRzUYY7XHYdUz
       
 debug 
       «
        as an alternative Julius offers delivery at Sun May 12 2024 13:28:56 GMT+0200 (Central European Summer Time) at 'the nice place'
       »
       
 info 
       ╭┈◜POST◝┈┈ 🟢 ┈┈( propositions/meetings/cook/post/id )┈┈
       ┊                ┈┈>( traits/post-response )┈┈┈┈┈┈
       ┊ 🕒 147ms
       ┊ 🔑 T_HolderJ91
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊🗣️  Request
       ┊ = 
         method = POST
         url = http://localhost:7777/api/v1/cook/meet
         
         🔝 headers
          = 
           [0] = Content-Type: application/json
           [1] = authorization: Bearer eyJhbGciOiJIUzUxMiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6IlRfSG9sZGVySjkxIiwibGFzdE5hbWUiOiJIb2xkZXItVGVzdGVyIiwiZmlyc3ROYW1lIjoiSnVsaXVzIiwicm9sZXMiOltdLCJpYXQiOjE3MTU1MTMzMzEsImV4cCI6MTcxNjExODEzMX0.4oyqWll7acTU9sGiR6F94VOhINmYV0DifTyxvn0O-S14fhsZb-flrbytOgPsM75jz7A1ahGjrXIFRrpmNeR28w
         
         📃 body
          = 
           name = new meeting
           meetPlace = the nice place
           meetFromDate = 2024-05-12T11:28:56.965Z
           meetToDate = 2024-05-12T11:43:56.965Z
           meetCoordinates = 
             lat = 41
             lng = 12
           cookPropositionId = JxsUWNxU4BjM6XUVMErehJ
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊🪃  Response
       ┊ = 
         statusCode = 201
         
         🔝 headers
          = 
           [0] = date: Sun, 12 May 2024 11:28:51 GMT
           [1] = request-id: 22220@LAPTOP-7D28KH4S/4ed5a4cac14854af5405f2bb-0000000000000033
           [2] = content-security-policy: report-uri http://localhost:7777/cspreport/send?time=1715513331000;
           [3] = cross-origin-embedder-policy: same-origin
           [4] = cross-origin-opener-policy: same-origin
           [5] = cross-origin-resource-policy: same-site
           [6] = x-dns-prefetch-control: off
           [7] = expect-ct: max-age=0
           [8] = x-frame-options: SAMEORIGIN
           [9] = strict-transport-security: max-age=15552000; includeSubDomains
           [10] = x-download-options: noopen
           [11] = x-content-type-options: nosniff
           [12] = origin-agent-cluster: ?1
           [13] = x-permitted-cross-domain-policies: none
           [14] = referrer-policy: strict-origin-when-cross-origin
           [15] = x-xss-protection: 0
           [16] = access-control-allow-origin: *
           [17] = access-control-allow-methods: GET,PUT,POST,DELETE,OPTIONS
           [18] = access-control-allow-headers: Origin, X-Requested-With, Content-Type, Accept
           [19] = sec-fetch-dest: image
           [20] = sec-fetch-mode: no-cors
           [21] = sec-fetch-site: cross-site
           [22] = content-type: application/json; charset=utf-8
           [23] = content-length: 177
           [24] = etag: W/"b1-LNDA1kONbpjCshQzHSvwygy1SPg"
           [25] = connection: close
         
         📃 body
          = 
           requestId = 22220@LAPTOP-7D28KH4S/4ed5a4cac14854af5405f2bb-0000000000000033
           id = WvzCBRynuBRdJsckbp4e6Q
           url = /api/v1/cook/meet/WvzCBRynuBRdJsckbp4e6Q
           result = success
       
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊👉 return = WvzCBRynuBRdJsckbp4e6Q
       
 debug 
       «
        🕒 rev.5
       >Server says time is  Mon, 13 May 2024 12:28:51 GMT<
        Local  says time is  Fri, 10 May 2024 08:28:59 GMT
        expect/actual jitter +273592ms / +273592ms  delta +0ms
       »
       
 debug   PROPOSITION
       ┈┈┈┈┈┈┈┈┈┈┈┈┈
       «
        Julius propose to cook 'My spectacular Rabbit with black bean and shallot' at Mon May 13 2024 14:28:56 GMT+0200 (Central European Summer Time)
       »
       
 info 
       ╭┈◜POST◝┈┈ 🟢 ┈┈( propositions/cook/post/id )┈┈
       ┊                ┈┈>( traits/post-response )┈┈┈┈┈┈
       ┊ 🕒 113ms
       ┊ 🔑 T_HolderJ91
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊🗣️  Request
       ┊ = 
         method = POST
         url = http://localhost:7777/api/v1/cook/proposition
         
         🔝 headers
          = 
           [0] = Content-Type: application/json
           [1] = authorization: Bearer eyJhbGciOiJIUzUxMiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6IlRfSG9sZGVySjkxIiwibGFzdE5hbWUiOiJIb2xkZXItVGVzdGVyIiwiZmlyc3ROYW1lIjoiSnVsaXVzIiwicm9sZXMiOltdLCJpYXQiOjE3MTU2MDMzMzEsImV4cCI6MTcxNjIwODEzMX0.uJu8qHAmooPCPT1W0-IaGlWcV-4bZwRX0NoTewd-FlzGsEhQY9F9A_PhDgECnsfF8s5lnzNb-8V_MMBOLlQrFw
         
         📃 body
          = 
           recipeId = 43uaEkxAJ2pDjQn87JE1Jc
           cook_hour = 14
           cook_minute = 28
           cook_day = 0
           servings = 1
           expected = 
             role_swap = false
             box_return = true
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊🪃  Response
       ┊ = 
         statusCode = 201
         
         🔝 headers
          = 
           [0] = date: Mon, 13 May 2024 12:28:51 GMT
           [1] = request-id: 22220@LAPTOP-7D28KH4S/4ed5a4cac14854af5405f2bb-0000000000000037
           [2] = content-security-policy: report-uri http://localhost:7777/cspreport/send?time=1715603331000;
           [3] = cross-origin-embedder-policy: same-origin
           [4] = cross-origin-opener-policy: same-origin
           [5] = cross-origin-resource-policy: same-site
           [6] = x-dns-prefetch-control: off
           [7] = expect-ct: max-age=0
           [8] = x-frame-options: SAMEORIGIN
           [9] = strict-transport-security: max-age=15552000; includeSubDomains
           [10] = x-download-options: noopen
           [11] = x-content-type-options: nosniff
           [12] = origin-agent-cluster: ?1
           [13] = x-permitted-cross-domain-policies: none
           [14] = referrer-policy: strict-origin-when-cross-origin
           [15] = x-xss-protection: 0
           [16] = access-control-allow-origin: *
           [17] = access-control-allow-methods: GET,PUT,POST,DELETE,OPTIONS
           [18] = access-control-allow-headers: Origin, X-Requested-With, Content-Type, Accept
           [19] = sec-fetch-dest: image
           [20] = sec-fetch-mode: no-cors
           [21] = sec-fetch-site: cross-site
           [22] = content-type: application/json; charset=utf-8
           [23] = content-length: 225
           [24] = etag: W/"e1-IvSf5RmTZ26okFGN4tvlBP+FrjQ"
           [25] = connection: close
         
         📃 body
          = 
           requestId = 22220@LAPTOP-7D28KH4S/4ed5a4cac14854af5405f2bb-0000000000000037
           id = Hxkce3uutWkt71DVJvG2R4
           url = /api/v1/cook/proposition/Hxkce3uutWkt71DVJvG2R4
           validToDate = 2024-05-15T12:28:00.000Z
           result = success
       
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊👉 return = Hxkce3uutWkt71DVJvG2R4
       
 debug 
       «
        Julius offers one bento for delivery at Mon May 13 2024 14:28:56 GMT+0200 (Central European Summer Time) at 'the nice place'
       »
       
 info 
       ╭┈◜POST◝┈┈ 🟢 ┈┈( propositions/meetings/cook/post/id )┈┈
       ┊                ┈┈>( traits/post-response )┈┈┈┈┈┈
       ┊ 🕒 132ms
       ┊ 🔑 T_HolderJ91
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊🗣️  Request
       ┊ = 
         method = POST
         url = http://localhost:7777/api/v1/cook/meet
         
         🔝 headers
          = 
           [0] = Content-Type: application/json
           [1] = authorization: Bearer eyJhbGciOiJIUzUxMiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6IlRfSG9sZGVySjkxIiwibGFzdE5hbWUiOiJIb2xkZXItVGVzdGVyIiwiZmlyc3ROYW1lIjoiSnVsaXVzIiwicm9sZXMiOltdLCJpYXQiOjE3MTU2MDMzMzEsImV4cCI6MTcxNjIwODEzMX0.uJu8qHAmooPCPT1W0-IaGlWcV-4bZwRX0NoTewd-FlzGsEhQY9F9A_PhDgECnsfF8s5lnzNb-8V_MMBOLlQrFw
         
         📃 body
          = 
           name = new meeting
           meetPlace = the nice place
           meetFromDate = 2024-05-13T12:28:56.965Z
           meetToDate = 2024-05-13T12:43:56.965Z
           meetCoordinates = 
             lat = 41
             lng = 12
           cookPropositionId = Hxkce3uutWkt71DVJvG2R4
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊🪃  Response
       ┊ = 
         statusCode = 201
         
         🔝 headers
          = 
           [0] = date: Mon, 13 May 2024 12:28:51 GMT
           [1] = request-id: 22220@LAPTOP-7D28KH4S/4ed5a4cac14854af5405f2bb-0000000000000038
           [2] = content-security-policy: report-uri http://localhost:7777/cspreport/send?time=1715603331000;
           [3] = cross-origin-embedder-policy: same-origin
           [4] = cross-origin-opener-policy: same-origin
           [5] = cross-origin-resource-policy: same-site
           [6] = x-dns-prefetch-control: off
           [7] = expect-ct: max-age=0
           [8] = x-frame-options: SAMEORIGIN
           [9] = strict-transport-security: max-age=15552000; includeSubDomains
           [10] = x-download-options: noopen
           [11] = x-content-type-options: nosniff
           [12] = origin-agent-cluster: ?1
           [13] = x-permitted-cross-domain-policies: none
           [14] = referrer-policy: strict-origin-when-cross-origin
           [15] = x-xss-protection: 0
           [16] = access-control-allow-origin: *
           [17] = access-control-allow-methods: GET,PUT,POST,DELETE,OPTIONS
           [18] = access-control-allow-headers: Origin, X-Requested-With, Content-Type, Accept
           [19] = sec-fetch-dest: image
           [20] = sec-fetch-mode: no-cors
           [21] = sec-fetch-site: cross-site
           [22] = content-type: application/json; charset=utf-8
           [23] = content-length: 177
           [24] = etag: W/"b1-1XtbCulwvktwlcT87sh2Hwtkc2I"
           [25] = connection: close
         
         📃 body
          = 
           requestId = 22220@LAPTOP-7D28KH4S/4ed5a4cac14854af5405f2bb-0000000000000038
           id = TASi8o18xW1hkum3yUECFJ
           url = /api/v1/cook/meet/TASi8o18xW1hkum3yUECFJ
           result = success
       
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊👉 return = TASi8o18xW1hkum3yUECFJ
       
 debug 
       «
        as an alternative Julius offers delivery at Mon May 13 2024 14:28:56 GMT+0200 (Central European Summer Time) at 'the nice place'
       »
       
 info 
       ╭┈◜POST◝┈┈ 🟢 ┈┈( propositions/meetings/cook/post/id )┈┈
       ┊                ┈┈>( traits/post-response )┈┈┈┈┈┈
       ┊ 🕒 128ms
       ┊ 🔑 T_HolderJ91
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊🗣️  Request
       ┊ = 
         method = POST
         url = http://localhost:7777/api/v1/cook/meet
         
         🔝 headers
          = 
           [0] = Content-Type: application/json
           [1] = authorization: Bearer eyJhbGciOiJIUzUxMiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6IlRfSG9sZGVySjkxIiwibGFzdE5hbWUiOiJIb2xkZXItVGVzdGVyIiwiZmlyc3ROYW1lIjoiSnVsaXVzIiwicm9sZXMiOltdLCJpYXQiOjE3MTU2MDMzMzEsImV4cCI6MTcxNjIwODEzMX0.uJu8qHAmooPCPT1W0-IaGlWcV-4bZwRX0NoTewd-FlzGsEhQY9F9A_PhDgECnsfF8s5lnzNb-8V_MMBOLlQrFw
         
         📃 body
          = 
           name = new meeting
           meetPlace = the nice place
           meetFromDate = 2024-05-13T12:28:56.965Z
           meetToDate = 2024-05-13T12:43:56.965Z
           meetCoordinates = 
             lat = 41
             lng = 12
           cookPropositionId = Hxkce3uutWkt71DVJvG2R4
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊🪃  Response
       ┊ = 
         statusCode = 201
         
         🔝 headers
          = 
           [0] = date: Mon, 13 May 2024 12:28:51 GMT
           [1] = request-id: 22220@LAPTOP-7D28KH4S/4ed5a4cac14854af5405f2bb-0000000000000039
           [2] = content-security-policy: report-uri http://localhost:7777/cspreport/send?time=1715603331000;
           [3] = cross-origin-embedder-policy: same-origin
           [4] = cross-origin-opener-policy: same-origin
           [5] = cross-origin-resource-policy: same-site
           [6] = x-dns-prefetch-control: off
           [7] = expect-ct: max-age=0
           [8] = x-frame-options: SAMEORIGIN
           [9] = strict-transport-security: max-age=15552000; includeSubDomains
           [10] = x-download-options: noopen
           [11] = x-content-type-options: nosniff
           [12] = origin-agent-cluster: ?1
           [13] = x-permitted-cross-domain-policies: none
           [14] = referrer-policy: strict-origin-when-cross-origin
           [15] = x-xss-protection: 0
           [16] = access-control-allow-origin: *
           [17] = access-control-allow-methods: GET,PUT,POST,DELETE,OPTIONS
           [18] = access-control-allow-headers: Origin, X-Requested-With, Content-Type, Accept
           [19] = sec-fetch-dest: image
           [20] = sec-fetch-mode: no-cors
           [21] = sec-fetch-site: cross-site
           [22] = content-type: application/json; charset=utf-8
           [23] = content-length: 177
           [24] = etag: W/"b1-Lr0mkvF57ttRzLC7VmVyK7uR264"
           [25] = connection: close
         
         📃 body
          = 
           requestId = 22220@LAPTOP-7D28KH4S/4ed5a4cac14854af5405f2bb-0000000000000039
           id = lshMrHGuivEsXG2TPwb79J
           url = /api/v1/cook/meet/lshMrHGuivEsXG2TPwb79J
           result = success
       
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊👉 return = lshMrHGuivEsXG2TPwb79J
       
 debug 
       «
        🕒 rev.1
       >Server says time is  Fri, 10 May 2024 08:29:00 GMT<
        Local  says time is  Fri, 10 May 2024 08:29:00 GMT
        expect/actual jitter +0ms / +0ms  delta +0ms
       »
       
 debug 
       «
        🕒 rev.1
       >Server says time is  Fri, 10 May 2024 08:28:51 GMT<
        Local  says time is  Fri, 10 May 2024 08:29:00 GMT
        expect/actual jitter -9ms / -9ms  delta +0ms
       »
       
 debug   REGISTRATION
       ┈┈┈┈┈┈┈┈┈┈┈┈┈┈
       «
        'Sai' registers as a new user on the web site 'Bento Solidaires'
       »
       
 info 
       ╭┈◜POST◝┈┈ 🟢 ┈┈( users/post )┈┈
       ┊                ┈┈>( users/post/response )┈┈┈┈┈┈
       ┊ 🕒 613ms
       ┊ 🔑 anonymous
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊🗣️  Request
       ┊ = 
         method = POST
         url = http://localhost:7777/api/v1/user
         
         🔝 headers
          = 
           [0] = Content-Type: application/json
         
         📃 body
          = 
           first_name = Sai
           last_name = Andrews-Tester
           email = Sai86.Andrews@pacific.sea
           userId = T_AndrewS86
           password = Welcome123!
           confirm_password = Welcome123!
           locale = en-US
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊🪃  Response
       ┊ = 
         statusCode = 201
         
         🔝 headers
          = 
           [0] = date: Fri, 10 May 2024 08:28:51 GMT
           [1] = request-id: 22220@LAPTOP-7D28KH4S/4ed5a4cac14854af5405f2bb-0000000000000043
           [2] = content-security-policy: report-uri http://localhost:7777/cspreport/send?time=1715329731000;
           [3] = cross-origin-embedder-policy: same-origin
           [4] = cross-origin-opener-policy: same-origin
           [5] = cross-origin-resource-policy: same-site
           [6] = x-dns-prefetch-control: off
           [7] = expect-ct: max-age=0
           [8] = x-frame-options: SAMEORIGIN
           [9] = strict-transport-security: max-age=15552000; includeSubDomains
           [10] = x-download-options: noopen
           [11] = x-content-type-options: nosniff
           [12] = origin-agent-cluster: ?1
           [13] = x-permitted-cross-domain-policies: none
           [14] = referrer-policy: strict-origin-when-cross-origin
           [15] = x-xss-protection: 0
           [16] = access-control-allow-origin: *
           [17] = access-control-allow-methods: GET,PUT,POST,DELETE,OPTIONS
           [18] = access-control-allow-headers: Origin, X-Requested-With, Content-Type, Accept
           [19] = sec-fetch-dest: image
           [20] = sec-fetch-mode: no-cors
           [21] = sec-fetch-site: cross-site
           [22] = set-cookie: bento-Bearer=eyJhbGciOiJIUzUxMiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6IlRfQW5kcmV3Uzg2IiwibGFzdE5hbWUiOiJBbmRyZXdzLVRlc3RlciIsImZpcnN0TmFtZSI6IlNhaSIsInJvbGVzIjpbXSwiaWF0IjoxNzE1MzI5NzMxLCJleHAiOjE3MTU5MzQ1MzF9.5tQ7mhqvVHGLK4LySWe10j8Yd0K4Ib0IarEzSRgJBpSHBnvzoDcCimgw7vwm_aETX04yA5Jtdd85erI5MQiQ1A; Max-Age=604; Path=/; Expires=Fri, 10 May 2024 08:38:55 GMT; HttpOnly
           [23] = content-type: application/json; charset=utf-8
           [24] = content-length: 492
           [25] = etag: W/"1ec-Nod+AQ1DFzzxhNMt1GHa3Q1fY9M"
           [26] = connection: close
         
         📃 body
          = 
           requestId = 22220@LAPTOP-7D28KH4S/4ed5a4cac14854af5405f2bb-0000000000000043
           token = eyJhbGciOiJIUzUxMiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6IlRfQW5kcmV3Uzg2IiwibGFzdE5hbWUiOiJBbmRyZXdzLVRlc3RlciIsImZpcnN0TmFtZSI6IlNhaSIsInJvbGVzIjpbXSwiaWF0IjoxNzE1MzI5NzMxLCJleHAiOjE3MTU5MzQ1MzF9.5tQ7mhqvVHGLK4LySWe10j8Yd0K4Ib0IarEzSRgJBpSHBnvzoDcCimgw7vwm_aETX04yA5Jtdd85erI5MQiQ1A
           inactive = true
           username = T_AndrewS86
           lastName = Andrews-Tester
           firstName = Sai
           code = 224925
           result = success
       
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊👉 return = 
         requestId = 22220@LAPTOP-7D28KH4S/4ed5a4cac14854af5405f2bb-0000000000000043
         token = eyJhbGciOiJIUzUxMiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6IlRfQW5kcmV3Uzg2IiwibGFzdE5hbWUiOiJBbmRyZXdzLVRlc3RlciIsImZpcnN0TmFtZSI6IlNhaSIsInJvbGVzIjpbXSwiaWF0IjoxNzE1MzI5NzMxLCJleHAiOjE3MTU5MzQ1MzF9.5tQ7mhqvVHGLK4LySWe10j8Yd0K4Ib0IarEzSRgJBpSHBnvzoDcCimgw7vwm_aETX04yA5Jtdd85erI5MQiQ1A
         inactive = true
         username = T_AndrewS86
         lastName = Andrews-Tester
         firstName = Sai
         code = 224925
         result = success
       
 debug 
       «
        Sai waits before activation...
       ⏰ fake sleep 45s
       »
       
 debug   ACTIVATION
       ┈┈┈┈┈┈┈┈┈┈┈┈
       «
        Sai attempts to activate his/her account with code '224925' received by email
       »
       
 info 
       ╭┈◜PUT◝┈┈ 🟢 ┈┈( users/put )┈┈
       ┊                ┈┈>( users/put/response )┈┈┈┈┈┈
       ┊ 🕒 164ms
       ┊ 🔑 Bearer
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊🗣️  Request
       ┊ = 
         method = PUT
         url = http://localhost:7777/api/v1/user/T_AndrewS86
         
         🔝 headers
          = 
           [0] = Content-Type: application/json
           [1] = authorization: Bearer eyJhbGciOiJIUzUxMiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6IlRfQW5kcmV3Uzg2IiwibGFzdE5hbWUiOiJBbmRyZXdzLVRlc3RlciIsImZpcnN0TmFtZSI6IlNhaSIsInJvbGVzIjpbXSwiaWF0IjoxNzE1MzI5NzMxLCJleHAiOjE3MTU5MzQ1MzF9.5tQ7mhqvVHGLK4LySWe10j8Yd0K4Ib0IarEzSRgJBpSHBnvzoDcCimgw7vwm_aETX04yA5Jtdd85erI5MQiQ1A
           [2] = mock-time-seconds: 45
         
         📃 body
          = 
           activation = 
             code = 224925
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊🪃  Response
       ┊ = 
         statusCode = 200
         
         🔝 headers
          = 
           [0] = date: Fri, 10 May 2024 08:29:36 GMT
           [1] = request-id: 22220@LAPTOP-7D28KH4S/4ed5a4cac14854af5405f2bb-0000000000000045
           [2] = content-security-policy: report-uri http://localhost:7777/cspreport/send?time=1715329776000;
           [3] = cross-origin-embedder-policy: same-origin
           [4] = cross-origin-opener-policy: same-origin
           [5] = cross-origin-resource-policy: same-site
           [6] = x-dns-prefetch-control: off
           [7] = expect-ct: max-age=0
           [8] = x-frame-options: SAMEORIGIN
           [9] = strict-transport-security: max-age=15552000; includeSubDomains
           [10] = x-download-options: noopen
           [11] = x-content-type-options: nosniff
           [12] = origin-agent-cluster: ?1
           [13] = x-permitted-cross-domain-policies: none
           [14] = referrer-policy: strict-origin-when-cross-origin
           [15] = x-xss-protection: 0
           [16] = access-control-allow-origin: *
           [17] = access-control-allow-methods: GET,PUT,POST,DELETE,OPTIONS
           [18] = access-control-allow-headers: Origin, X-Requested-With, Content-Type, Accept
           [19] = sec-fetch-dest: image
           [20] = sec-fetch-mode: no-cors
           [21] = sec-fetch-site: cross-site
           [22] = content-type: application/json; charset=utf-8
           [23] = content-length: 98
           [24] = etag: W/"62-fMlusfcdqDfGlerCoI2sTVHqNaI"
           [25] = connection: close
         
         📃 body
          = 
           requestId = 22220@LAPTOP-7D28KH4S/4ed5a4cac14854af5405f2bb-0000000000000045
           result = success
       
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊👉 return = 
         requestId = 22220@LAPTOP-7D28KH4S/4ed5a4cac14854af5405f2bb-0000000000000045
         result = success
       
 debug 
       «
        Sai is happy !
       He/she has registered and activated an account,
       meaning he/she can access the Bento Solidaires website and start contributing.
       »
       
 debug 
       «
        🕒 rev.1
       >Server says time is  Fri, 10 May 2024 08:29:01 GMT<
        Local  says time is  Fri, 10 May 2024 08:29:01 GMT
        expect/actual jitter +0ms / +0ms  delta +0ms
       »
       
 debug   PARTNERS
       ┈┈┈┈┈┈┈┈┈┈
       «
        Here are 2 users of Bento Solidaires:
         - Julius has a cook profile
         - Sai has a guest profile
       »
       
 debug 
       «
        It's Mon May 13 2024 16:28:56 GMT+0200 (Central European Summer Time), Sai wants to eat Julius's My spectacular Rabbit with black bean and shallot proposed at Mon May 13 2024 14:28:56 GMT+0200 (Central European Summer Time)
       »
       
 debug 
       «
        🕒 rev.2
       >Server says time is  Mon, 13 May 2024 14:28:56 GMT<
        Local  says time is  Fri, 10 May 2024 08:29:01 GMT
        expect/actual jitter +280796ms / +280795ms  delta +1ms
       »
       
 info 
       ╭┈◜POST◝┈┈ 🟢 ┈┈( propositions/eat/post/id )┈┈
       ┊                ┈┈>( traits/post-response )┈┈┈┈┈┈
       ┊ 🕒 115ms
       ┊ 🔑 T_AndrewS86
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊🗣️  Request
       ┊ = 
         method = POST
         url = http://localhost:7777/api/v1/eat/proposition
         
         🔝 headers
          = 
           [0] = Content-Type: application/json
           [1] = authorization: Bearer eyJhbGciOiJIUzUxMiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6IlRfQW5kcmV3Uzg2IiwibGFzdE5hbWUiOiJBbmRyZXdzLVRlc3RlciIsImZpcnN0TmFtZSI6IlNhaSIsInJvbGVzIjpbXSwiaWF0IjoxNzE1NjEwNTM2LCJleHAiOjE3MTYyMTUzMzZ9.0CyDO76Jgj3Us3r88LfO38NA4sxAUuQx0C6kr-Ae_RpMav_UK6uTKLAqTnlzwmWv3ur0-d1QJZMKXKgOVqhHfw
         
         📃 body
          = {}
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊🪃  Response
       ┊ = 
         statusCode = 201
         
         🔝 headers
          = 
           [0] = date: Mon, 13 May 2024 14:28:56 GMT
           [1] = request-id: 22220@LAPTOP-7D28KH4S/4ed5a4cac14854af5405f2bb-0000000000000050
           [2] = content-security-policy: report-uri http://localhost:7777/cspreport/send?time=1715610536000;
           [3] = cross-origin-embedder-policy: same-origin
           [4] = cross-origin-opener-policy: same-origin
           [5] = cross-origin-resource-policy: same-site
           [6] = x-dns-prefetch-control: off
           [7] = expect-ct: max-age=0
           [8] = x-frame-options: SAMEORIGIN
           [9] = strict-transport-security: max-age=15552000; includeSubDomains
           [10] = x-download-options: noopen
           [11] = x-content-type-options: nosniff
           [12] = origin-agent-cluster: ?1
           [13] = x-permitted-cross-domain-policies: none
           [14] = referrer-policy: strict-origin-when-cross-origin
           [15] = x-xss-protection: 0
           [16] = access-control-allow-origin: *
           [17] = access-control-allow-methods: GET,PUT,POST,DELETE,OPTIONS
           [18] = access-control-allow-headers: Origin, X-Requested-With, Content-Type, Accept
           [19] = sec-fetch-dest: image
           [20] = sec-fetch-mode: no-cors
           [21] = sec-fetch-site: cross-site
           [22] = content-type: application/json; charset=utf-8
           [23] = content-length: 224
           [24] = etag: W/"e0-cnMLpRw1QhV2g+pisg9zjgwogSA"
           [25] = connection: close
         
         📃 body
          = 
           requestId = 22220@LAPTOP-7D28KH4S/4ed5a4cac14854af5405f2bb-0000000000000050
           id = SeC7SG4zW6MhMSEVhrdQk9
           url = /api/v1/eat/proposition/SeC7SG4zW6MhMSEVhrdQk9
           validToDate = 2024-05-20T14:28:56.000Z
           result = success
       
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊👉 return = SeC7SG4zW6MhMSEVhrdQk9
       
 info 
       ╭┈◜POST◝┈┈ 🟢 ┈┈( deal/post/id )┈┈
       ┊                ┈┈>( traits/post-response )┈┈┈┈┈┈
       ┊ 🕒 343ms
       ┊ 🔑 T_AndrewS86
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊🗣️  Request
       ┊ = 
         method = POST
         url = http://localhost:7777/api/v1/deal
         
         🔝 headers
          = 
           [0] = Content-Type: application/json
           [1] = authorization: Bearer eyJhbGciOiJIUzUxMiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6IlRfQW5kcmV3Uzg2IiwibGFzdE5hbWUiOiJBbmRyZXdzLVRlc3RlciIsImZpcnN0TmFtZSI6IlNhaSIsInJvbGVzIjpbXSwiaWF0IjoxNzE1NjEwNTM2LCJleHAiOjE3MTYyMTUzMzZ9.0CyDO76Jgj3Us3r88LfO38NA4sxAUuQx0C6kr-Ae_RpMav_UK6uTKLAqTnlzwmWv3ur0-d1QJZMKXKgOVqhHfw
         
         📃 body
          = 
           cook_proposition_id = Hxkce3uutWkt71DVJvG2R4
           eat_proposition_id = SeC7SG4zW6MhMSEVhrdQk9
           meet_id = TASi8o18xW1hkum3yUECFJ
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊🪃  Response
       ┊ = 
         statusCode = 201
         
         🔝 headers
          = 
           [0] = date: Mon, 13 May 2024 14:28:56 GMT
           [1] = request-id: 22220@LAPTOP-7D28KH4S/4ed5a4cac14854af5405f2bb-0000000000000051
           [2] = content-security-policy: report-uri http://localhost:7777/cspreport/send?time=1715610536000;
           [3] = cross-origin-embedder-policy: same-origin
           [4] = cross-origin-opener-policy: same-origin
           [5] = cross-origin-resource-policy: same-site
           [6] = x-dns-prefetch-control: off
           [7] = expect-ct: max-age=0
           [8] = x-frame-options: SAMEORIGIN
           [9] = strict-transport-security: max-age=15552000; includeSubDomains
           [10] = x-download-options: noopen
           [11] = x-content-type-options: nosniff
           [12] = origin-agent-cluster: ?1
           [13] = x-permitted-cross-domain-policies: none
           [14] = referrer-policy: strict-origin-when-cross-origin
           [15] = x-xss-protection: 0
           [16] = access-control-allow-origin: *
           [17] = access-control-allow-methods: GET,PUT,POST,DELETE,OPTIONS
           [18] = access-control-allow-headers: Origin, X-Requested-With, Content-Type, Accept
           [19] = sec-fetch-dest: image
           [20] = sec-fetch-mode: no-cors
           [21] = sec-fetch-site: cross-site
           [22] = content-type: application/json; charset=utf-8
           [23] = content-length: 172
           [24] = etag: W/"ac-SwRAaSdtWeSeEzOLiGhiYToFftc"
           [25] = connection: close
         
         📃 body
          = 
           requestId = 22220@LAPTOP-7D28KH4S/4ed5a4cac14854af5405f2bb-0000000000000051
           id = VSLwYpuVway93Mioe3yJZ9
           url = /api/v1/deal/VSLwYpuVway93Mioe3yJZ9
           result = success
       
       ├⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯┈┈┈┈┈
       ┊👉 return = VSLwYpuVway93Mioe3yJZ9
       
 debug 
       «
        Sai has a deal for Julius's My spectacular Rabbit with black bean and shallot, it's dealId={"eat_proposition_id":"SeC7SG4zW6MhMSEVhrdQk9","deal_id":"VSLwYpuVway93Mioe3yJZ9"}
       »
       
 PASS   E2E  livingdoc/tests/end-to-end/_landscape/profile.A.test.ts (32.016 s)
  profile A
    √ let user do social cooking on Bento Solidaires (10201 ms)


> Test run finished at 5/10/2024, 10:29:01 AM <

Test Suites: 1 passed, 1 total
Tests:       1 passed, 1 total
Snapshots:   0 total
Time:        32.995 s
```

That's the proof the API does the job for the nominal case.

Now let's define all the kind of bumps that could make the deal derail :
  
```javascript

export const caseGroups = <CaseGroup[]>[

  {
    groupName: 'nominal',
    //=====================
    cases: [
      {
        caseName: 'no discard',
        //-----------------
      },
    ]
  },

  {
    groupName: 'discard before deal seal',
    //===================================
    cases: [
    {
      caseName: 'cook discards deal / before deal seal',
      //----------------------------------------------
      discardWhen: DiscardWhen.beforeDealSeal,
      discardFrom: DiscardFrom.cook,
      discardWhat: DiscardWhat.deal,
      discardStory: `I see Liz demand at 20: 00.
...wait... I'm so dumb I forgot I have double appointment...
I have to go to the dentist at 19: 00 as well.
That's bad for my reputation but I have no choice but to break the deal. I discard it.`
    },

    {
      caseName: 'guest discards deal / before deal seal',
      //-----------------------------------------------
      discardWhen: DiscardWhen.beforeDealSeal,
      discardFrom: DiscardFrom.guest,
      discardWhat: DiscardWhat.deal,
      discardStory: `I am so unlucky, my train line is on strike today.
I can't make it today as we arranged for pickup.
That's bad for my reputation but I have no choice but to break the deal. I discard it.
Nevertheless tomorrow I hope I can deal with another cook for a similar lunch.`
    },

    {
      caseName: 'cook discards proposition / before deal seal',
      //-----------------------------------------------------
      discardWhen: DiscardWhen.beforeDealSeal,
      discardFrom: DiscardFrom.cook,
      discardWhat: DiscardWhat.proposition,
      discardStory: `I see Liz demand at 20: 00.
...wait... checking the fridge...
I belatedly notice I miss a critical ingredient. My sea urchin stock is depleted.
A fisher friend of mine brought me plenty last time but I won't have any more soon.
That's bad for my reputation but I have no choice but to break the deal. I discard it.
Notice that in the present case, I won't make any other deal of the cook proposition.
To tell it clearly I discard the deal AND the proposition`
    },

    {
      caseName: 'guest discards proposition / before deal seal',
      //------------------------------------------------------
      discardWhen: DiscardWhen.beforeDealSeal,
      discardFrom: DiscardFrom.guest,
      discardWhat: DiscardWhat.proposition,
      discardStory: `I am so unlucky, I caught a flu, I can't go out.
I won't pickup the awaited bento as arranged.
I have no choice but to break the deal. I discard it.
Notice that in the present case, I won't make any other deal on the eat proposition.
Doctor told me I'd be bedridden for a week.
To tell it clearly I discard the deal AND the proposition`
    },
  ]},

  {
    groupName: 'discard after deal seal / before cooked',
    //==================================================
    cases: [
    {
      caseName: 'cook discards / after deal seal / before cooked',
      //--------------------------------------------------------
      discardWhen: DiscardWhen.beforeCooked,
      discardFrom: DiscardFrom.cook,
      discardWhat: DiscardWhat.deal,
      discardStory: `...dummit... I'm so dumb I forgot I have double appointment...
I have to go to the dentist same time as delivery.
That's bad for my reputation but I have no choice but to break the sealed deal. I discard it.`
    },

    {
      caseName: 'guest discards deal / after deal seal / before cooked',
      //--------------------------------------------------------------
      discardWhen: DiscardWhen.beforeCooked,
      discardFrom: DiscardFrom.guest,
      discardWhat: DiscardWhat.deal,
      discardStory: `I am so unlucky, my train line is on strike the day I arranged pickup.
That's bad for my reputation but I have no choice but to break the sealed deal. I discard it.
Nevertheless tomorrow I hope I can deal with another cook for a similar lunch.`
    },

    {
      caseName: 'cook discards proposition / after deal seal / before cooked',
      //--------------------------------------------------------------------
      discardWhen: DiscardWhen.beforeCooked,
      discardFrom: DiscardFrom.cook,
      discardWhat: DiscardWhat.proposition,
      discardStory: `...I'm about to cook... checking the fridge...
I belatedly notice I miss a critical ingredient. My sea urchin stock is depleted.
A fisher friend of mine brought me plenty last time but I won't have any more soon.
That's bad for my reputation but I have no choice but to break the deal. I discard it.
Notice that in the present case, I won't make any other deal of the cook proposition.
To tell it clearly I discard the deal AND the proposition`
    },

    {
      caseName: 'guest discards proposition / after deal seal / before cooked',
      //---------------------------------------------------------------------
      discardWhen: DiscardWhen.beforeCooked,
      discardFrom: DiscardFrom.guest,
      discardWhat: DiscardWhat.proposition,
      discardStory: `I am so unlucky, I caught a flu, I can't go out.
I won't pickup the awaited bento as arranged.
I have no choice but to break the deal. I discard it.
Notice that in the present case, I won't make any other deal on the eat proposition.
Doctor told me I'd be bedridden for a week.
To tell it clearly I discard the deal AND the proposition`
    },
  ]},

  {
    groupName: 'discard after deal seal / after cooked / before delivery',
    //===================================================================
    cases: [
    {
      caseName: 'cook discards / after deal seal / after cooked / before delivery',
      //-------------------------------------------------------------------------
      discardWhen: DiscardWhen.afterCooked,
      discardFrom: DiscardFrom.cook,
      discardWhat: DiscardWhat.deal,
      discardStory: `I cooked but... dummit... I'm so dumb I forgot I have double appointment...
I have to go to the dentist same time as delivery.
That's bad for my reputation but I have no choice but to break the sealed deal. I discard it.`
    },

    {
      caseName: 'guest discards deal / after deal seal / after cooked / before delivery',
      //-------------------------------------------------------------------------------
      discardWhen: DiscardWhen.afterCooked,
      discardFrom: DiscardFrom.guest,
      discardWhat: DiscardWhat.deal,
      discardStory: `I saw you cooked but... I am so unlucky, my train line is on strike the day I arranged pickup.
That's bad for my reputation but I have no choice but to break the sealed deal. I discard it.
I hope we can arrange a pickup for the next day. Will it still be fresh enough?
I perfectly understand you give it to somebody else. It's all my fault. Sorry.`
    },

    {
      caseName: 'cook discards proposition / after deal seal / after cooked / before delivery',
      //-------------------------------------------------------------------------------------
      discardWhen: DiscardWhen.afterCooked,
      discardFrom: DiscardFrom.cook,
      discardWhat: DiscardWhat.proposition,
      discardStory: `I cooked it but.. to tell it franckly it's a failure.
I prefer to cancel delivery. Really sorry for that.
My supply is depleted. I won't cook it anytime soon.
I discard the deal AND the proposition
That's bad for my reputation but there was a situation`
    },

    {
      caseName: 'guest discards proposition / after deal seal / after cooked / before delivery',
      //--------------------------------------------------------------------------------------
      discardWhen: DiscardWhen.afterCooked,
      discardFrom: DiscardFrom.guest,
      discardWhat: DiscardWhat.proposition,
      discardStory: `I saw you cooked but... it looks so different to the recipe.
I prefer to cancel pickup. Really sorry for that.
I discard the deal AND the proposition cause finally I will go to the restaurant
That's bad for my reputation but I do what I want`
    },
    ]
  },

]
```

and the show goes on...
[Test output removed for brevity]
## Type compliance with Json-Schema

You probably wonder how I tested the API calls, well Pactum hopefully does a lot of what you need. It's perfect for your AAA Arrange-Act-Assess testing activities. Nevertheless I needed to assess precisely that the json output complied to the schema.

I chose to write my types in Json-Schema first, then to derive (automatically) into Typescript types for coding strong-typing purpose (not compulsory). So the tests effectively check against the Json-Schema, which makes it a language agnostic API testing method.

I feel confortable I could answer a request to test an API without knowing which language it was made with indeed. Json-Schema is more expressive than C# type definition for example, it can express union types, it can test with regular expressions. It is possible to derive to any target language. 

As an example here is the schema of a successful answer to a cook evaluation submission:

```yaml
$id: schemas/evaluations/cook/put-response-success
type: object
properties:
  requestId:
    $ref: schemas/scalar/rid
  id:
    $ref: schemas/traits/id
  url:
    $ref: schemas/scalar/uri
  patch:
    type: object
    properties:
      evaluations:
        type: object
        properties:
          cook:
            type: object
            properties:
              box_return:
                $ref: schemas/evaluations/rate
              set_return:
                $ref: schemas/evaluations/rate
              role_swap:
                $ref: schemas/evaluations/rate
              place:
                $ref: schemas/evaluations/rate
              time:
                $ref: schemas/evaluations/rate
              commentsPublic:
                type: string
              commentsPrivate:
                type: string
            required:
              - box_return
              - set_return
              - role_swap
              - place
              - time
              - commentsPublic
              - commentsPrivate
          updated:
            type: object
            properties:
              cook:
                type: string
                format: date-time
            required:
              - cook
        required:
          - cook
          - updated
      result:
        type: string
        const: success
    required:
      - evaluations
required:
  - id
  - url
  - patch

```

In this article, I demonstrate how PactumJS could be leveraged to accomplish E2E testing of an API, and how I used Json-Schema for type compliance. I hope you enjoyed. Don't hesitate to ask me mailto:vinz.thedev@gmail.com about it. Have nice testing.