# Commands

Aliucord offers a rich commands api which makes it easy to implement your own commands. It hooks into slash commands so all commands will be
made available along with the regular slash commands.

## The basics

Every plugin has its own [CommandsAPI](https://aliucord.github.io/Javadoc/com/aliucord/api/CommandsAPI.html) made available as `commands` inside your plugin class.

You can register commands using `commands.registerCommand(name, description, options, callback)` and unregister them later either by using `commands.unregisterCommand(commandName)` or via `commands.unregisterAll()`.
Commands should be unique, so please use a meaningful command name that won't overlap with other plugins.

Commands are run on a separate thread, so you can do heavy work here, send Http Requests, etc...

Errors are caught and will be presented to the user in a nicely formatted error, but you should still make sure your command never throws errors.

The callback is a lambda function that gets the CommandContext as only argument and should return a [CommandResult](https://aliucord.github.io/Javadoc/com/aliucord/api/CommandsAPI.CommandResult.html) or null to send no reply.

Please refer to the [CommandContext Javadoc](https://aliucord.github.io/Javadoc/com/aliucord/entities/CommandContext.html) for the available methods

## CommandOptions

Command Options are options the user can specify. They can be used to make the user input any text, select from a selection of values, select another user, etc.
These are kind of a mess and take a lot of arguments because they come from Discord.
Simply pass null, Collections.emptyList() or whatever may be suitable.

Quick rundown (Note: You cannot create CommandChoices yourself, use [Utils.createCommandChoice](https://aliucord.github.io/dokka/html/-aliucord/com.aliucord/-utils/create-command-choice.html))
```java
new ApplicationCommandOption(
        ApplicationCommandType type, // The type of this argument, e.g. String, User or SubCommand
        String name, // The name of this argument. This will both be shown to the user and be the key of this argument in the callback
        String description, // The description of this command
        Integer descriptionRes, // Resource ID of the description string. If discord has a string you find suitable, use this to have the description be localized, otherwise pass null
        boolean required, // Whether this option is required (the user MUST fill it out)
        boolean def, // Whether this option is the default selected option ( I think ?? )
        List<CommandChoice> choices, // List of choices the user can choose from
        List<ApplicationCommandOption> options // Nested command options, only applicable for SubCommands
)
```