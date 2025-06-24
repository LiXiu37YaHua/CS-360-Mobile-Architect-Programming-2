# CS-360-Mobile-Architect-Programming-2
CS 360 Programming
## Module Eight Journal: CS 360 Mobile App Portfolio Artifact

### App Summary & User Needs  
For my Project Three app, I built **MyLoginApp**, an inventory/goal‐tracking mobile application with user authentication and optional SMS alerts. The primary requirements were to let new users register and returning users log in, persist their data in an SQLite database, and display items (or events/weights) in a grid. Users can add, edit, or delete entries, and—with permission—receive SMS notifications when a defined threshold is reached. This addresses the need for a simple, persistent, and secure way to track personal or business data on the go.

### Screens & User-Centered UI  
- **Login Screen** with clear username/password fields and separate “Log In” and “Register” buttons.  
- **Database Screen** featuring a two-column RecyclerView grid of items and a persistent “Add Item” button.  
- **Add/Edit Dialogs** that prompt for just the necessary fields (name & quantity) in a clean AlertDialog.  
I kept the UI minimal—large tap targets, concise labels, and straightforward navigation—so users of any skill level can immediately understand how to register, log in, and manage their data.

### Coding Approach & Future Techniques  
I began by sketching my data flow and database schema, then built a single `SQLiteOpenHelper` class to handle users and items. I used modular methods (`createUser()`, `checkCredentials()`, `insertItem()`, etc.) so each piece could be tested independently. This strategy—divide and conquer—will serve me well in future apps when I need to isolate features or swap out storage layers (e.g., moving from SQLite to Room or a cloud backend).

### Testing & What It Revealed  
I tested continuously in the Android emulator:  
1. **Login/Registration** flows (valid vs. duplicate usernames)  
2. **CRUD operations** on the RecyclerView grid  
3. **Permission dialogs** for SMS (grant vs. deny)  
4. **Actual SMS sends** via ADB commands and emulator sensor controls  
This process caught edge cases (e.g., empty usernames, permission denials) early and confirmed that unregistering listeners in `onPause()` stopped background SMS triggers—preventing crashes and battery drain.

### Innovation & Challenge Overcome  
I struggled initially with testing SMS without a real device. To innovate, I learned to use ADB’s `emu sms send` command and stubbed hardware calls so the app would degrade gracefully when `SEND_SMS` wasn’t granted. That stub-first mindset let me validate the rest of the app even before hardware was available.

### Highlighted Component  
I’m particularly proud of the **SMS-permission logic**:  
- Runtime check/request in `DatabaseActivity`  
- A boolean flag to gate calls to `SmsManager`  
- Graceful fallback that left the UI fully functional  
This demonstrates my ability to integrate Android’s modern security model with real-world features.



