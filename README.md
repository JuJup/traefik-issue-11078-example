## Explanation

Check the issue https://github.com/traefik/traefik/issues/11078 for which this repo was made for.
You need to adjust the Host in the Ingressroute to match your current setup, but then you should be able to deploy the resource files.

There are two deployments (my-app, my-nginx), which for simplicity both run a nginx container.
Now change the replicas of the deployments and observe, if the ingressroute is working or not.

- App 1, Nginx 1: Ingressroute working
- App 0, Nginx 1: Ingressroute working
- App 1, Nginx 0: Ingressroute failed, because Middleware is not found
- App 0, Nginx 0: Ingressroute failed, because Middleware is not found

Whenever we remove the Pod from the Service that is used by the Errors Middleware, our Setup doesn't work anymore. This is crucial, when we use tools like `Sablier`.