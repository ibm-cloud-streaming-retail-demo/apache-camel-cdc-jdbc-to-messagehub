# Example change data capture 

## jdbc to messagehub

- https://stackoverflow.com/questions/45999725/how-to-poll-database-using-apache-camel
- https://issues.apache.org/jira/browse/CAMEL-11682

## jdbc to s3

- http://camel.apache.org/aws-s3.html

## s3 to messaehub

- http://camel.apache.org/aws-s3.html

E.g. 

from("direct:pollEnrich").routeId("pollEnrich") 
                            .pollEnrich() 
.simple("aws-s3://{{buckets.mybucket}}?amazonS3Client=#amazonS3Client&deleteAfterRead=false&fileName=${in.header.CamelAwsS3Key}")
                            .convertBodyTo(byte[].class) 
                            .to(...)

