---
title: Docker Bowline
date: 2024-08-31 10:00:00 +0200
categories: [Projects]
tags: [docker, node.js, typescript]     
---


[marcusrognes/docker-bowline](https://github.com/marcusrognes/docker-bowline)

## Description

A simple library for sending requests to docker engine over sockets.

Disclaimer, this only has implemented features I currently need for running on demand matchmaking servers.


## Getting started

```bash
npm i docker-bowline
```

## Example

`main.ts`
```ts
import { Docker } from 'docker-bowline';

async function main(){
	// Unix: /var/run/docker.sock
	// Windows: //./pipe/docker_engine
	const docker = new Docker({socket: "/var/run/docker.sock"});
	
	// Create container won`t auto pull a missing container.
	await docker.images.pull("mongo:latest");
	
	const container = await docker.containers.create(
		"test-mongo",
		{
			Image: "mongo"
		}
	);
	
	await docker.containers.start(container.Id);
	
	const inspectContainerResponse = await docker.containers.inspect(container.Id);
	
	await docker.containers.stop(container.Id);
	
	await docker.containers.delete(container.Id);
}

main().then(() => console.log("Done"));
```


## Why?

I was looking into creating a game service system that would need to be able to handle matchmaking servers.

I decided that docker would be a super simple way of handling the servers, and experimented with managing docker containers and services with node.

I found the existing solutions out there a bit lacking and outdated.

This was the results of my experimentations, a simple node package without any dependencies.

It is still very much a work in progress, and I have only implemented the features from docker I have needed so far.
