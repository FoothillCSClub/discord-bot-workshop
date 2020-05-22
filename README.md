Welcome to this workshop! We're going to build a Discord bot with [discord.py](https://discordpy.readthedocs.io/en/latest/) and Python. Let's dive right into it!

# Build a Discord Bot

## Prerequisites

- Python and Pip
- A Discord account

## Step 1: Create a Bot Account

1.  Make sure you’re logged on to the [Discord website](https://discord.com/).

2.  Navigate to the [application page](https://discord.com/developers/applications)

3.  Click on the “New Application” button.

    ![The new application button.](https://discordpy.readthedocs.io/en/v1.3.3/_images/discord_create_app_button.png)

4.  Give the application a name and click “Create”.

    ![The new application form filled in.](https://discordpy.readthedocs.io/en/v1.3.3/_images/discord_create_app_form.png)

5.  Create a Bot User by navigating to the “Bot” tab and clicking “Add Bot”.

    ![The Add Bot button.](https://discordpy.readthedocs.io/en/v1.3.3/_images/discord_create_bot_user.png)

    - Click “Yes, do it!” to continue.

6.  If you want others to invite your bot, make sure that **Public Bot** is ticked. Also, make sure that **Require OAuth2 Code Grant** is unchecked.

    ![How the Bot User options should look like for most people.](https://discordpy.readthedocs.io/en/v1.3.3/_images/discord_bot_user_options.png)

7.  Copy the token using the “Copy” button.

    - **NOTE: This is not the same thing as the Client Secret on the General Information page**
    - **WARNING: This token is equivalent to your bot's password, so do not share it with anyone.**

## Step 2: Invite Your Bot

1.  Go to the “OAuth2” tab

    ![How the OAuth2 page should look like.](https://discordpy.readthedocs.io/en/latest/_images/discord_oauth2.png)

2.  Tick the “bot” checkbox under “scopes”

    ![The scopes checkbox with "bot" ticked.](https://discordpy.readthedocs.io/en/latest/_images/discord_oauth2_scope.png)

3.  Tick the permissions required for your bot to function under “Bot Permissions”

    ![The permission checkboxes with some permissions checked.](https://discordpy.readthedocs.io/en/latest/_images/discord_oauth2_perms.png)

4.  Now the resulting URL can be used to add your bot to a server. Copy and paste the URL into your browser, choose a server to invite the bot to, and click “Authorize”.

Source: [https://discordpy.readthedocs.io/en/latest/discord.html](https://discordpy.readthedocs.io/en/latest/discord.html)

## Step 3: Setup Your Environment

1. Install or upgrade discord.py: `pip3 install -U discord.py`
	- NOTE: you may need to use a variation of the pip command depending on your platform.
2. Create a Python file and name it anything, such as `coolio_bot.py`
3. Open the file in your favorite code editor

## Step 4: Let's Get Coding

1. Start off by importing the discord.py library:

	```python
	import discord

	client = discord.Client()

	# Add event handlers here

	client.run('Your token from Step 1')
	```

2. Listen to the `ready` event

	```python
	# Event handlers
	@client.event
	async def on_ready():
	    print('We have logged in as {0.user}'.format(client))
	```

3. Listen for a new `message`:
	```python
	@client.event
	async def on_message(message):
	    if message.author == client.user:
	        return

	    if message.content.startswith('$hello'):
	        await message.channel.send('Hello!')
	```

### Final Bootstrap Code:

```python
import discord

client = discord.Client()

# Event handlers
@client.event
async def on_ready():
    print('We have logged in as {0.user}'.format(client))

@client.event
async def on_message(message):
    if message.author == client.user:
        return

    if message.content.startswith('$hello'):
        await message.channel.send('Hello!')

client.run('Your token from Step 1')
```

## Step 5: Start Hacking

So now that you've got your bot set up, what's next? Well, of course, start building! Take the next 30 minutes and see what you can come up with. Be ready to share your bot's commands with others for them to try out what you make!
