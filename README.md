### The Problem

Question: How can I reach the subdomain test123 hosted by the 'S3Ninja' container from the 'MyContainer' container?
I get an error the host could not be resolved. 


✅  I can reach the subdomain from a terminal on my computer:
```bash
curl test123.localhost:9000                                                                
<?xml version="1.0" encoding="UTF-8"?><Error>
    <Code>AccessDenied</Code>
    <Message>Authentication required</Message>
    <Resource>/test123</Resource>
</Error>
```

✅ I can reach the 'S3Ninja' container from the 'MyContainer' container:
```bash
docker exec -it MyContainer sh   
```
```bash
curl S3Ninja:9000                                                                
<?xml version="1.0" encoding="UTF-8"?><ListAllMyBucketsResult xmlns="http://s3.amazonaws.com/doc/2006-03-01/">
    <hint>Goto: http://S3Ninja:9000/ui to visit the admin UI</hint>
    <Owner>
        <ID>initiatorId</ID>
        <DisplayName>initiatorName</DisplayName>
    </Owner>
    <Buckets/>
</ListAllMyBucketsResult>

```

❌ However, the the subdomain test123 hosted by the 'S3Ninja' container is *not* reachable from the 'MyContainer' container.
```bash
docker exec -it MyContainer sh       
```
```bash
curl test123.S3Ninja:9000    
curl: (6) Could not resolve host: test123.S3Ninja
```

... 😢