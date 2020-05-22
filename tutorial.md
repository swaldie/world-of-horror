# Tutorial

I wanted to flesh out the included documentation a little bit, in order to make it a little easier for new modders.  I recommended opening one of the included event files in the [modding pack](https://www.wohgame.com/modding.zip) to follow along with as you read through this to help contextualize thing.  One thing to note is that right now, virtually every option you specify is a string, and should be encased in quotes.

## Initial Headers

Each component in the initial heads establish basic information about the event:

`name=` - The title of the event.  This appears in the top left corner of the screen
`author=` - Your name! The authors of the scenarios.
`contact=` - A field to put some sort of contact information for yourself.  These are commonly discord handles right now. However, some folks, like me, might use a web address or email.
`about=` - Short text that will appear in the mods menu that describes the event.  The developer recommends you keep this value short.
`flavor=` - This is the initial text that appears that describes the event to the players.  The text here will auto-wrap to a new line, but you can manually specify a new line using the `#` character.
`location=` - The zone in the game that you can encounter the event.  You can select the following options:
* downtown
* school
* hospital
* seaside
* forest
* mansion
* village
* apartment

There are also 4 unique event types, which you can encounter regardless of location if you have the corresponding old god selected.
* ithotu
* athyola
* gozu
* atorasu
`options=` - This is the number of options, stored as a string and thus encapsulated in quotes.  Supports up to three options right now.  (As an example, use `"1"`, `"2"`, or `"3"`)
`big=` - This optional field allows you to choose if the event is shown with full screen art or not.  Set this to `"1"` to use.
`image=` - The file path to the image file you're using.  (An example from the modding folder: `image="other art\public_computer_sleep.png"`).  If you instead set `""` as the option, it will select a generic image based off where the event is encountered.

## Options (The actual choices a player gets to make)

Earlier we specified the `options` flag, which set the number of options we have.  When you're configuring the options, you append `a`, `b`, or `c` to the option value to specify which choice number it is.  (So `optiona` corresponds to the first choice, `optionb` the second, etc.)

Each option segment consists of several pieces, similar to the header above.  The key difference here is that you'll repeat this for each choice the player can make. I'm going to use the `optiona` example for this section:

`optiona=` - The actual on screen dialog for the choice.
`testa=` - The stat, or fund check that's performed to see if you succeed in the challenge in the game.  There are a number of options:
Stats:
* strength
* dexterity
* perception
* knowledge
* charisma
* luck

Additionally, you can set the event to not have a test by setting `testa` to `story`.

Finally, if you want, instead of a test, an invite where a player has to use some of their funds to succeed, you can set `funds1`, to try and take 1 Funds from the player, or `funds2` to remove 2 funds.

`successa=` - The dialog that should display for a successful test. Like the flavour, you can use `#` to add new lines. It's worth mentioning that whatever reward the player obtains will display automatically.  For example (`+10 Experience` will automatically be added.)
`failurea=` - The dialog that displays if a player fails the test. Like the flavour, you can use `#` to add new lines. It's worth mentioning that whatever reward the player obtains will display automatically.  For example (`+10 Experience` will automatically be added.)
`winprizea=` or `failprizea` - What the player wins if the succeed.  Lots of options here:
* stamina
* doom
* reason
* experience
* funds
* injury
* curse
* ally
* item

`winnumbera=` or `failnumbera` - This specifies the amount you want to increment the above for success or failure.  Worth noting that right now `injury`, `curse`, and `ally` are random effects, so just use `""` for the arguments.  If you used `item` above, you need to specify the item name in all caps (example: `STEAK KNIFE`). If you misspell the item name, the game will create an item with the misspelled name with no properties, so make sure you double check that item spelling!


