# config-client
Spring boot config client


If central config properties in GIT get changed then to reflect the change in the config client (other microservices)
we need to do following things.

1. Add @RefreshScope on the bean which is using the properties from central config git repository.
2. Add actuator dependecy in the client microservices.
3. If any changes happens to the GIT properties file, then these chagnes need to the refreshed by calling the POST call of actuator/refresh end point which will rerefresh the bean which is annotated with @RefreshScope bean.
4. Now call the post call from the client service as "http://localhost:9080/actuator/refresh" POST call it will return the refresh key or properties.
5. Now you call the your client service where you are using properties from central git repository, you will get the updated values.

The other way to handle this refresh is to use spring -bus in combination of rabbitMQ or Kafka message.


Example of config client and config-server is avalilabel here.
