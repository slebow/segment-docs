---

title: Movable Ink Destination
id: 5a611c86c0ff800001f6c431
---
[Movable Ink](https://movableink.com/){:target="_blank"} lets marketers deliver jaw-dropping, personalized customer experiences. Movable Ink automatically transforms data into personalized content for email and mobile marketing.

This destination is maintained by [Movable Ink](https://movableink.com/){:target="_blank"}. If you have any issues, reach out to your Movable Ink Client Experience team.

{% include content/beta-note.md %}

## Pre-Requisites
A Movable Ink Stories license is required to leverage this integration. Please reach out to your Movable Ink client experience team with any questions.

You will need to share sample event payloads with your Movable Ink Client Experience team before enabling the destination in Segment. Your Client Experience team will then work with a Solutions Architect to map the event within Movable Ink and share an endpoint URL, access key ID and access secret. This event mapping in Movable Ink and API credentials are required for a successful response. 

To find sample event payloads within Segment:
1. Share sample event payloads with your Movable Ink client experience manager. To locate sample event payloads in Segment:
  - Navigate to ‘Sources’ and click on the source you’d like to stream data from.
  - Click ‘Debugger’. You will see a list of incoming sample events.
  - Click on the event you’re interested in. Click ‘Raw’ on the right-hand side of the screen to view a full sample payload
  - Copy this sample payload and share securely with your client experience team.
2. Once Movable Ink has mapped your event payload, your Client Experience Manager will then provide you with a Movable Ink endpoint URL, access Key ID and access secret. 

## Getting Started
1. From the Segment web app, click Catalog, then click Destinations.
2. Find the Destinations Actions item in the left navigation, and click it.
3. Click ‘Configure Movable Ink (Actions)’.
4. Select an existing Source to connect to Movable Ink (Actions).
5. Name your destination
6. Select whether you would like to manually set up the destination or repurpose settings for an earlier integration.
7. Click ‘Create Destination’.

## Configuring Movable Ink API credentials in Segment
1. Within the Settings, input your Movable Ink API credentials into the following fields:
  - Username: paste your Movable Ink Access Key ID
  - Access Secret: paste your Movable Ink Access Secret
  - Movable Ink URL: paste your Movable Ink Endpoint URL
2. Click ‘Save settings’

## Select events to stream to Movable Ink
1. Navigate to ‘Mappings’ and click ‘New Mapping’
2. Click ‘Send Entire Event’
3. Select your events
  - Select the events you’d like to send to Movable Ink by adding or removing any event types (ex. Track, Identify, etc.) you’d like to send.
  - You can select a specific event by clicking ‘Add Condition’ and adding rules based on Event Names. You can create rules to send multiple events.
4. Add a test event. Preview your sample data by loading a test event from source or loading a sample event
5. Select mappings. You can map specific fields or properties to send from Segment to Movable Ink. This step is not necessary, and is only needed if you would like to update any of the fields that are referenced from the original event payload.
6. Send a test event by clicking ‘Test Mapping’.
  - _Note_: You may see an error message if your Movable Ink Ink Solutions team has mapped the event in Movable Ink yet, or if there is an error with the mapping. Please reach out to your Movable Ink client experience team with the full sample payload if you are seeing unexpected errors.
7. Save your event. You will be returned to the Mappings overview page, where you will need to Enable your mapping.
8. You can map any other events you would like to include if these were not included in your first mapping.
9. When you have finalized your integration set-up, navigate to your integration’s Settings table and toggle ‘Enable destination’.


## Events Specifications

### Identify
If you're not familiar with the Segment Specs, take a look to understand what the [Identify method](/docs/connections/spec/identify/) does.

When you send an `identify` event with one of Segments sources, this is passed to the Movable Ink API and includes the user `traits` you provide along with the previously used `anonymousId` as well as the `userId` that was given.

Once the Movable Ink API receives this `identify` event, it will associate the events made by the previous `anonymousId` to the provided `userId` or `traits.email` if one is provided. From that point on, the events will now appear in the user profile. This enables **Stories** features such as behavioral targeting, as well as content integrations like **Behavioral Apps**.

### Track
If you're not familiar with the Segment Specs, take a look to understand what the [Track method](/docs/connections/spec/track/) does.

When you send a `track` event with one of Segment's sources, Movable Ink will normalize them into the same events that Movable Ink's API would normally receive. They will then be available to target against in behavioral marketing campaign content as well as being available in **Custom Apps** and **Behavioral Apps**.

Track events that are sent to Movable Ink will be attributed to the user identifier provided by any `identify` call. This user identifier may be an email or another unique identifier if one exists for that user.

If no `identify` call has been made, then the events will be attributed to an anonymous user using the `anonymousId`, until an `identify` call is made and the `userId` is set.

### Event Requirements
Movable Ink can now accept standard eCommerce events (product view, cart add, conversion, search, category view) and custom events (any other events tracked in Segment). However, all events must include the following requirements:
- Timestamp: The time when the event occurred
- Either a user ID or an anonymous ID must be present
  - User ID: The unique identifier of the profile that triggered this event.
  - Anonymous ID: A unique identifier of the anonymous profile that triggered this event.

### Example Flow
1. Send a `track` event with no identity, it will attribute to an anonymous user.
2. Send an `identify` event to set the user identifier.
3. Send another `track` event. It will be attributed to the user set by the `identify` event.

### Considerations
Movable Ink only retains event data for use in personalized use cases for 30 days. Movable Ink's Segment Personas integration may be a good alternative for use cases that leverage persistant user attributes or traits within Segment, rather than event data.

Movable Ink cannot process sensitive personally identifiable information. If your event payload includes any sensitive data, within the destination please navigate to Filters and click ‘New Filter’ to limit specific events, properties or user traits from being sent to Movable Ink.

If you have any questions about the event data or feasibility for your use case, please share sample event payloads with your Movable Ink client experience team.
