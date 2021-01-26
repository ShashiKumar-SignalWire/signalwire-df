# Signalwire (Text Messaging) Integration

## Setup

### Prerequisites

- Follow the instructions on the [main README file](https://github.com/GoogleCloudPlatform/dialogflow-integrations#readme) in the root directory of this repository.
- Create a [Signalwire account](https://www.signalwire.com).
- Replace the value of __projectId__ in the [server.js file](https://github.com/ShashiKumar-SignalWire/signalwire-df/blob/master/README.md#L32) with your Dialogflow agent’s Project ID.


### Buying a Phone Number

1. Log in to the your Signalwire Space.
2. Navigate to Phone Numbers
3. Click on the + New button, Search for a number that has SMS capabilities and buy it.


### Deploying the Integration Using Cloud Run

In your local terminal, change the active directory to the repository’s root directory.

Run the following command to save the state of your repository into [GCP Container Registry](https://console.cloud.google.com/gcr/). Replace PROJECT-ID with your agent’s GCP Project ID and PLATFORM with the platform subdirectory name.

```shell
gcloud builds submit --tag gcr.io/PROJECT-ID/dialogflow-PLATFORM
```

Deploy your integration to live using the following command. Replace PROJECT-ID with your agent’s GCP project Id, PLATFORM with the platform subdirectory name, and YOUR_KEY_FILE with the name (not path) of your Service Account JSON key file.

```shell
gcloud beta run deploy --image gcr.io/PROJECT-ID/dialogflow-PLATFORM --update-env-vars GOOGLE_APPLICATION_CREDENTIALS=YOUR_KEY_FILE --memory 1Gi
```

- When prompted for a target platform, select a platform by entering the corresponding number (for example, ``1`` for ``Cloud Run (fully managed)``).
 - When prompted for a region, select a region (for example, ``us-central1``).
 - When prompted for a service name hit enter to accept the default.
 - When prompted to allow unauthenticated invocations press ``y``.
 - Copy the URL given to you, and use it according to the README file in the
 given integration's folder.

More information can be found in Cloud Run
[documentation](https://cloud.google.com/run/docs/deploying).

You can view a list of your active integration deployments under [Cloud Run](https://console.cloud.google.com/run) in the GCP Console.

### Setting up Phone Number

1. In the "Phone Number" section, Click on your phone number to integrate Dialog flow agent.
2. Click on the  purchased number 
3. Click on Edit Setings
4. Underneath "Messaging", take the value for the server URL printed in the console after the completion of the execution of the last command from the above section to the __"A message comes in"__ fill-in box. Set the first drop-down to __Webhook__ and the HTTP method to __HTTP POST__. 

https://github.com/ShashiKumar-SignalWire/signalwire-df/blob/master/images/ConfigureNumberForMessageIntegration.PNG

