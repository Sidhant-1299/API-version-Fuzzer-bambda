# API-version-Fuzzer-bambda
Multithreaded burpsuite bambda to quickly test for API versioning

### Usage:
- Load the bambda into the custom action
- If there is already a version in the url eg: `example.com/api/v1/user/1` you're in luck. Just run the custom action.
- If you want to insert a request just add xxx in the url: `example.com/api/xxx/user/1`

By default the versioning is from 0 to 5. So the default payloads are `['v0','v1','v2','v3','v4','v5','']`
*Note*: there is also an empty versioning by default

you can change them from the initlization of the class:
```
    private int minAPIVersion = 0;
    private int maxAPIVersion = 5;
```
---
### Returns 
- length of the response content
- Status code of the response

### Example log
```
Using 'v' as version prefix.
Testing versions from 0 -> 5
Testing URL: http://crapi.apisec.ai/identity/api/user/dashboard -> Status: 401, Length: 30
Testing URL: http://crapi.apisec.ai/identity/api/v5/user/dashboard -> Status: 401, Length: 30
Testing URL: http://crapi.apisec.ai/identity/api/v4/user/dashboard -> Status: 401, Length: 30
Testing URL: http://crapi.apisec.ai/identity/api/v0/user/dashboard -> Status: 401, Length: 30
Testing URL: http://crapi.apisec.ai/identity/api/v1/user/dashboard -> Status: 401, Length: 30
Testing URL: http://crapi.apisec.ai/identity/api/v3/user/dashboard -> Status: 401, Length: 30
Testing URL: http://crapi.apisec.ai/identity/api/v2/user/dashboard -> Status: 401, Length: 30
All requests completed.
```
