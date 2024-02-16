## msr-config-server
### Running on local
You need to set these environment variables on your IDE
spring.profiles.active=`the spring profile`
com.msr.eureka.url=`https://localhost:8181/discovery/eureka`
com.msr.config.user=`the git user`
com.msr.config.password=`the git password/token`
com.msr.config.url=`https://github.com/msrfintech/msr-config-files.git`
### Running Docker
Image **msrfintech/config-server**
Your need to set the below environment variables
spring.profiles.active=`the spring profile`
com.msr.eureka.url=`https://localhost:8181/discovery/eureka`
com.msr.config.user=`the git user`
com.msr.config.password=`the git password/token`
com.msr.config.url=`https://github.com/msrfintech/msr-config-files.git`