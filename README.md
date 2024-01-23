# Skcrew-python
This API allow you to make async web requests to Skcrew Web API

Example of usage:
```py
from skcrew import api
from skcrew.datatypes import Signal
import asyncio

skcrewapi = api("localhost","admin","admin")
# async method
async def main():
	servers = await skcrewapi.servers()
	online_serves = await skcrewapi.servers(online=True)
	server = await skcrewapi.server(server='Lobby')
	players = await skcrewapi.players()
	players_from_lobby = await skcrewapi.players(server='lobby')
	player = await skcrewapi.player(player='Lotzy') # or player object or uuid as string
	await skcrewapi.kick(player = player, reason = 'go out dude')
	await skcrewapi.connect(player = player, server = 'lobby') # server as server object or server name
	signal = Signal(key = "broadcast",data = ["Hello world!"])
	await skcrewapi.signals(signals=[signal], servers=['lobby']) # signals as Signal object or Dict or Json string / # server as server object or server name
asyncio.run(main())
```