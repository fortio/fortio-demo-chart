# fortio-demo-chart
Sample fortio chart for kubernetes and a depth of 3 layers of services with both TCP and http:

![image](https://github.com/fortio/fortio-demo-chart/assets/3664595/bcfd56c6-864b-46a7-a068-ad21f2bbc1df)

If you enter in layer A (the client UI) http://fortio-b-http-parallel:8088/echo?size=100&status=555:2
which means go through the b layer parallel proxy which in turn will make 2 requests to C1, C2 
(will reach both http://fortio-c1-http:8080/echo and http://fortio-c2-http:8080/echo in parallel) 
and get responses of 100bytes with 2% of 555 and 98% of success/200s 
(from either so outcome should be higher than 2% combined error rate)

![image](https://github.com/fortio/fortio-demo-chart/assets/3664595/3e4e9694-2b87-464e-a776-e5c806559aa0)

You get the following expected graph for the run:

![image](https://github.com/fortio/fortio-demo-chart/assets/3664595/d4adb5d1-a2d4-4e4f-9ca9-eed18f168349)

And on Kiali

![image](https://github.com/fortio/fortio-demo-chart/assets/3664595/c0bc30f1-cca8-4769-bddb-1a8b003f76b9)


Then if you use Jaeger or Tempo you can see:

![image](https://github.com/fortio/fortio-demo-chart/assets/3664595/5a64207c-0269-4296-98c4-372f469245e9)

