---
title: EXISTS
linkTitle: EXISTS
description: EXISTS
menu:
  latest:
    parent: api-redis
    weight: 2060
aliases:
  - /latest/api/redis/exist
  - /latest/api/yedis/exist
isTocNested: true
showAsideToc: true
---
Single-key request only. Requests with multiple keys are not yet supported.

## Synopsis
<b>`EXISTS key [key ...]`</b><br>
This command is a predicate to check whether or not the given `key` exists.

## Return Value
Returns the number of existing keys.

## Examples

You can do this as shown below.
<div class='copy separator-dollar'>
```sh
$ SET yuga1 "Africa"
```
</div>
```sh
"OK"
```
<div class='copy separator-dollar'>
```sh
$ SET yuga2 "America"
```
</div>
```sh
"OK"
```
<div class='copy separator-dollar'>
```sh
$ EXISTS yuga1
```
</div>
```sh
1
```
<div class='copy separator-dollar'>
```sh
$ EXISTS yuga1 yuga2 not_a_key
```
</div>
```sh
2
```

## See Also
[`del`](../del/), [`get`](../get/), [`getrange`](../getrange/), [`hdel`](../hdel/), [`hexists`](../hexists/), [`hget`](../hget/), [`hset`](../hset/), [`hincrby`](../hincrby/), [`sadd`](../sadd/), [`set`](../set/)