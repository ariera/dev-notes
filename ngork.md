### To open your ssh:
1. you need to create an account on ngork.com `https://ngrok.com/signup`
2. you will have an auth token
3. `./ngrok -authtoken YOUR_AUTH_TOKEN -proto=tcp 22`
4. ngor will show you something like: `Forwarding tcp://ngrok.com:55004 -> 127.0.0.1:22` 
5. to connect `ssh -p 55004 ariera@ngrok.com`
6. you can all share VNC via port: 5900

