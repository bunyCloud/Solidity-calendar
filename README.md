
#Calendar Factory
The Calendar factory is useful for when you need to deploy separate calendar for each user.

#Telos Calendar Implementation
The Telos calendar contract is used by the Calendar Factory as a template implementation for deployments. 

#CalendarOne
CalendarOne is the most recent calendar proof of concept. This calendar is designed as a public contract for use by many users. There is no factory as only one contract is deployed. Here is a summary of CalendarOne contract functions:

Sure, here is the same text formatted with Markdown:

# CalendarOne Contract Overview

This smart contract represents a calendar system where users can create events, invite others events, update, and accept invitations to calendar events.

- **calendarName**: A public variable that stores the name of the calendar.

- **userEvents**: A mapping of Ethereum addresses to arrays of CalendarEvent structs. This represents the events associated with each user.

- **users**: An array that keeps track of all users who have created events.

- **eventCreators**: An array that stores all the addresses of the users who have created an event.

- **eventCount**: A mapping that tracks the number of events created by each user.

- **eventInvitations**: A mapping of event IDs to arrays of Ethereum addresses. This represents the users invited to each event.

- **totalEvents**: A counter that keeps track of the total number of events created across all users.


## Main Functions

Here are the main functions provided by this smart contract:

1. `createTelosCalendarEvent`: 
   * A user can create an event, defining the title, start time, end time, metadata URI (for instance, a link to an IPFS file or a JSON file URL) and the addresses of the invited attendees. 
   * This function updates various mappings and arrays to keep track of the events and their creators, increments the total events count, and emits events when a new event is created and users are invited.

2. `acceptInvitation`: 
   * A user can accept an invitation to an event by providing the event ID. 
   * This function checks if the event exists and if the user has been invited to the event, then it adds the user's address to the confirmed attendees' list and emits an "InvitationAccepted" event.

3. `updateEvent`: 
   * A user can update an existing event they've created by providing the event ID and the new details of the event (title, start time, end time, metadata URI). 
   * The function emits an "EventUpdated" event.

4. `getUserEvents`: 
   * This view function allows anyone to fetch the events created by a specific user by providing the user's address. 
   * The function returns an array of `CalendarEvent` structs.

5. `getAllUsersEvents`: 
   * This view function allows anyone to fetch all events created by all users. 
   * It returns an array of `AllEvents` structs, each containing a user's address and their array of events.

## Additional Features

In addition, this smart contract has a few public state variables for storing the calendar name, mapping users to their events, tracking all users and event creators, and keeping count of the total number of events. It also contains a few custom structs to organize information about individual calendar events and the overall set of events.

Lastly, it emits several events that can be listened for: `NewEventCreated`, `EventUpdated`, `UserInvited`, and `InvitationAccepted`.
