## This follows the workflow of the Architecture.

- Experience Layer (Devices): 
  How it behaves:
    - These devices will talk to your backend over HTTPS protocol.
    - THey do notcommunicate directly with field equipment.

- Process Layer (IoT API, Machine Gateway, Translation, Permissions):
  How It Behaves:
    - IoT API (Magneta Service):
      This is the front door for all app and system calls.
    - Machine Gateway (Lambda):
      The first Lambda hop after the API for device-relatd operations.
        - Maps user or app requests.
        - Handles retirs/basic error handling around talking to the IoT backend.
    - Translation (Lambda Chain):
      Lambda job to normalise and enrich data.
      Different fucntions for device types and message types.
    - Permissions (Magenta Services):
      This handles authentication and permissons policies.

## WORK SKETCH
    1) IoT API receives the call
    2) IoT API asks permission.
    3) If allowed, IoT API hands off to Machine Gateway and then Translation.
    4) Response is sent back to the Experience Layer.
