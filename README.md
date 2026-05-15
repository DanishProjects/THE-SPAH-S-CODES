# THE-SPAH-S-CODES
this is probably my latest project DISCORD


i fotgot how to make a code section,so i decided to add just to the readme :)

import config
print(config.TOKEN)

import discord
from discord.ext import commands

intents = discord.Intents.default()
intents.message_content = True
intents.members = True  # needed for !joined command

client = commands.Bot(command_prefix='!', intents=intents)

@client.event
async def on_ready():
    print(f'We have logged in as {client.user}')

@client.event
async def on_message(message):
    if message.author == client.user:
        return

    if message.content.startswith('hello'):
        await message.channel.send('gentleman?')

    if message.content.startswith('wut_happened?'):
        await message.channel.send('the red spy is in the base and stolen our briefcase!')

    if message.content.startswith('what?!'):
        await message.channel.send('hes right behind us...')

    if message.content.startswith('what should we do now?!'):
        await message.channel.send('we have to protect the briefcase!')

    if message.content.startswith('but its not easy to fight him!'):
        await message.channel.send('thiz is outrageous!')

    if message.content.startswith('be something overpowered!'):
        await message.channel.send('i know!')

    if message.content.startswith('what is it?!'):
        await message.channel.send('FRENCHMAN 100% حلال ACTIVATED!')

    if message.content.startswith('uhh,what?'):
        await message.channel.send('SAY WALLAHI BRO!')

    if message.content.startswith('how did bro instantly become islam?'):
        await message.channel.send('well i mualaf certainly!')

    await client.process_commands(message)

@client.command()
async def about(ctx):
    await ctx.send('this is da bot made with discord.py')

@client.command()
async def info(ctx):
    await ctx.send('name=danish(gajehdude)\nage:12(just yesterday)\nwhat i love to do:gamin! and drawin!\nwanna be:a teacher')

@client.command()
async def joined(ctx, member: discord.Member = None):
    member = member or ctx.author
    
    # DEBUG: this will show up in your terminal
    print(f"[DEBUG] Member: {member}, Joined_at: {member.joined_at}")
    
    if member.joined_at is None:
        await ctx.send(f"Can't see when {member.display_name} joined. Check that SERVER MEMBERS INTENT is ON in Discord Developer Portal and restart the bot.")
        return
    
    joined_date = member.joined_at.strftime("%d %B %Y, %H:%M UTC")
    await ctx.send(f"**{member.display_name}** joined this server on **{joined_date}**")

client.run(config.TOKEN)
