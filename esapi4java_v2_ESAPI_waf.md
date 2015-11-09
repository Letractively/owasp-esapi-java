## There is an application-level web application firewall (WAF) in ESAPI for Java ##

ESAPI for Java includes an application-level WAF. It can be used for:

  * Virtual patches
  * Enforce authentication
  * Enforce access control
  * Egress filtering/detection
  * Enforce HTTPS

The figure below depicts how the ESAPI for Java WAF fits into the big picture alongside of other ESAPI for Java controls.

http://owasp-esapi-java.googlecode.com/svn/trunk/documentation/esapi4java-waf.JPG

Having the WAF and ESAPI together provides developers the tools the need to deal with a variety of situations. The WAF can provide immediate virtual patching, to give the developers the time they need to fix things ‘right’ at a more reasonable pace. ESAPI then gives the tools to fix things right.  In some environments, the developers can’t change the code, so the WAF supports that situation.

We would almost always recommend solving most security issues in the app itself, rather than externalizing the security in a WAF, but the WAF is very useful to deal with security situations that come up after the application has been implemented.
It also has capabilities not yet imagined by today's WAFs because it is deployed much closer to the application. Because of its proximity, the ESAPI WAF can use custom code and session storage to integrate meaningful, complex and customized security into an application. Don't have the source? Not a problem! ESAPI can sit in front without any code changes. Don't have $200k to buy a commercial WAF? Don't feel comfortable with mod\_security? ESAPI WAF is your answer! Assuming some knowledge of WAFs, the talk will cover its capabilities (with demonstrations), testing strategy (to provide assurance) and integration strategies.

## More on virtual patching ##

The term "virtual patching" has been around for a while, but when Ivan Ristic (author of ModSecurity) included it in a list of use cases for WAFs over a year ago it got Jeff thinking about it.  Essentially, it just means writing a specific WAF rule that targets a known vulnerability. This allows you to quickly block an attack in progress or a critical flaw you've discovered until you have time to fix the code correctly.  To me, this is a capability that every web application should have.

The ESAPI WAF is particularly well designed for this use case, as it is integrated into the application, as opposed to deployed as a standalone box. That means that you don't have to reparse the HTTP request, you have access to authentication and session information, and you can take actions within the application.