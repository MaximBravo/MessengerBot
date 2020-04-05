# MessengerBot
 POC Messenger Bot

Create a keys.json file in the functions directory that looks like this:

> {
>   "verify_token": "<YOUR_VERIFY_TOKEN>"
> }

Navigate to functions directory and run following command:

> firebase deploy --only functions

To test:

> curl -X GET "https://us-central1-rasagcp.cloudfunctions.net/messengerWebhook/webhook?hub.verify_token=test_key_123&hub.challenge=CHALLENGE_ACCEPTED&hub.mode=subscribe" 
Should return:
> CHALLENGE_ACCEPTED

> curl -H "Content-Type: application/json" -X POST "https://us-central1-rasagcp.cloudfunctions.net/messengerWebhook/webhook" -d "{\"object\": \"page\", \"entry\": [{\"messaging\": [{\"message\": \"TEST_MESSAGE\"}]}]}"
Should return:
> EVENT_RECEIVED
