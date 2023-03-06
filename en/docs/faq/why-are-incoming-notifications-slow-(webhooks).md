# Why are incoming notifications slow (webhooks)?

Our service is waiting for a 200 response from your server for 20 seconds, if no confirmation is received, then after 1 minute it tries to send the same notification again. So a 200 response from your server should be given within 20 seconds of you receiving the incoming notification. To correctly configure the incoming notification handler, you need to remove the logic for processing incoming notifications at the time of receipt, namely, use the following scheme:

- accept notification from our service
- keep the notification on your side, you can use the queue
- reply to our service 200
- process an incoming notification from its storage. It is not recommended to process notifications immediately upon receipt if this causes a delay in receiving notifications