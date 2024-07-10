## Setting Up and Updating Discord Rich Presence

### `setup_discord_presence` Method

```python
def setup_discord_presence(self):
    self.client_id = "1260552765160034405"  # Replace with your own client ID
    self.discord_presence = Presence(client_id=self.client_id)
    try:
        self.discord_presence.connect()
        self.update_presence()
    except Exception as e:
        print(f"Error connecting to Discord RPC: {e}")
```

- **Purpose**: Initializes the Discord Rich Presence client and connects it to Discord.
- **Steps**:
  1. **Client ID**: Sets `self.client_id` to your Discord application's client ID.
  2. **Presence Initialization**: Creates an instance of `Presence` from `pypresence` using the provided client ID.
  3. **Connection**: Attempts to connect to Discord using `self.discord_presence.connect()`.
  4. **Update Presence**: Calls `self.update_presence()` to initially update the presence information.

### `update_presence` Method

```python
def update_presence(self):
    presence_data = {
        "state": "Listening to music",
        "details": f"Now playing: {self.current_song}" if self.current_song else "Browsing songs",
        "large_image": "red"  # Replace with the key of your large image
    }
    self.discord_presence.update(**presence_data)
```

- **Purpose**: Updates the Discord Rich Presence with current activity information.
- **Presence Data**:
  - `state`: Indicates the user's current activity state, such as "Listening to music".
  - `details`: Specifies detailed information, dynamically updating based on whether a song is currently playing (`self.current_song`).
  - `large_image`: Represents a large image key displayed in Discord.
