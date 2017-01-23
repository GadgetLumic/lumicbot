README.md
from asyncio import coroutine
from .plugins import LumicbotPlugin

myplugin = LumicbotPlugin("My Plugin", author="Me")

@myplugin.trigger
@coroutine
def trigger(text):
    """Return True here to indicate that your plugin could want to react to this line"""

@myplugin.helplines
@coroutine
def help_lines():
    return ["/command1 - Do something awesome", "/command2 - Do something even more awesome"]

@myplugin.group_chat
@coroutine
def reaction(text, sender, respond):
    """Program your actual reaction in this coroutine"""
    yield from respond("Hello, %s!", sender.firstname)
