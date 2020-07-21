cf-ops -> $ source setenv.rc 

```
/data/config/testhsb /data/cf-ops
/data/cf-ops
Using environment '10.122.100.6' as client 'admin'

Name               testhsb  
UUID               8ab12720-7c11-4830-bba8-130853aff09c  
Version            270.2.0 (00000000)  
Director Stemcell  ubuntu-xenial/315.64  
CPI                aws_cpi  
Features           compiled_package_cache: disabled  
                   config_server: enabled  
                   local_dns: enabled  
                   power_dns: disabled  
                   snapshots: enabled  
User               admin  

Succeeded
```



logsearch-ops -> $ source setenv.rc

```
/data/config/testhsb /data/logsearch-ops
/data/logsearch-ops
Using environment '10.122.100.6' as client 'admin'

Name               testhsb  
UUID               8ab12720-7c11-4830-bba8-130853aff09c  
Version            270.2.0 (00000000)  
Director Stemcell  ubuntu-xenial/315.64  
CPI                aws_cpi  
Features           compiled_package_cache: disabled  
                   config_server: enabled  
                   local_dns: enabled  
                   power_dns: disabled  
                   snapshots: enabled  
User               admin  

Succeeded
```



**credhub admin login**

- credhub login --client-name credhub-admin --client-secret ${BOSH_CREDHUB_CLIENT_SECRET}

```
Login Successful
```

**uaac admin-client-secret 정보 얻기**

- credhub get --name /${BOSH_ENVIRONMENT}/cf/uaa_admin_client_secret -q

```
w46an6W313UMfI3KfHdyvBnihqGDRx
```

**UAA 서버에서 클라이언트 액세스 토큰 인증 및 확보**

- uaac token client get admin -s w46an6W313UMfI3KfHdyvBnihqGDRx

```
Successfully fetched token via client credentials grant.
Target: https://uaa.testhsb.test.devground.io
Context: admin, from client admin
```

**UAA 서버 타겟팅**

- uaac target

```
Target: https://uaa.testhsb.test.devground.io
Context: admin, from client admin
```

