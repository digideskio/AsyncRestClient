[ ![Download](https://api.bintray.com/packages/eginez/maven/org.eginez.groovy.AsyncRestClient/images/download.svg) ](https://bintray.com/eginez/maven/org.eginez.groovy.AsyncRestClient/_latestVersion)
# AsyncRestClient
This is a light weight extension of groovy's RESTClient to support asyn call via RxGroovy

Install:

```groovy
dependencies {
        compile 'org.eginez.groovy:AsyncRestClient:1.+'
}
```

For RESTClient documentation: https://github.com/jgritman/httpbuilder/wiki/RESTClient. 
For RxGroovy documentation: https://github.com/ReactiveX/RxGroovy

Quick example:

```groovy
with(AsyncRest) {
new RESTClient('https://google.com')
        .getAsync(path:'/')
        .subscribe { res -> println res.data }
        }
```
And of course harness the power of RxJava :D
```groovy
with(AsyncRest){
Observable<Object>.zip(
    new RESTClient('http://someurl.com/part_1').getAsync(),
    new RESTClient('http://someurl.com/part_2').getAsync(),
    { res1, res2
        //proccess them eg:
        [res1.data: res2.data]
    })
    .subscribe { println '2 concurrent rest calls sync\'d for processing'}
    }
```

