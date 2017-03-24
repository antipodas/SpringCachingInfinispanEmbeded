# SpringCachingInfinispanEmbeded

– Build project with Maven configure:

clean install

– Run Project with mode: Spring Boot App

– Open JConsole 
then chooses SpringCachingInfinispanApplication

Press Connect then choose MBeans:

– Make a put Customers request:

http://localhost:8080/putCust?custNumber=100
Observe Cache customer, numberOfEntries has value: 100

See Log:

PUT customer with id = 1953044158854880992 to Cache

PUT customer with id = -1846995831834450987 to Cache

PUT customer with id = 3044941980965491438 to Cache

PUT customer with id = -6522290097430820157 to Cache

PUT customer with id = 7581231483461521828 to Cache

– Make a findCustomerById request:

http://localhost:8080/findCustById?id=1

Result:

Because the customer with (key = 1) does Not exist in Cache, So Log has:

Loading customer with id '1'

– Make a findCustomerById request:

http://localhost:8080/findCustById?id=1

Observer caching, press Refresh: numberOfEntries has value: 101

– Make a findCustomerById request again:

http://localhost:8080/findCustById?id=1

Result the same with above request, because customer with id=1 has been cached.

Observer caching, press Refresh on JConsole: numberOfEntries has value: 101

– Make Evict request to an element:

http://localhost:8080/evictEntry?id=1

Observer caching, press Refresh on JConsole: numberOfEntries has value: 100.

– Make Evict request with all Entries:

http://localhost:8080/evictAll

Observer caching, press Refresh: numberOfEntries has value: 0.

