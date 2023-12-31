

# CalendarOne Contract Overview

This smart contract represents a calendar system where users can create events, invite other users to events, update, and accept invitations to calendar events.

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

Events to listen for:  `NewEventCreated`, `EventUpdated`, `UserInvited`, and `InvitationAccepted`.
