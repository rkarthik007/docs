---
title: SET
linkTitle: SET
description: SET
menu:
  latest:
    parent: api-redis
    weight: 2270
aliases:
  - /latest/api/redis/set
  - /latest/api/yedis/set
isTocNested: true
showAsideToc: true
---

## Synopsis
<b>`SET key string_value [EX seconds] [PX milliseconds] [NX|XX]`</b><br>
This command inserts `string_value` to be hold at `key`, where `EX seconds` sets the expire time in `seconds`, `PX milliseconds` sets the expire time in `milliseconds`, `NX` sets the key only if it does not already exist, and `XX` sets the key only if it already exists.

<li>If the `key` is already associated with a value, it is overwritten regardless of its type.</li>
<li>All parameters that are associated with the `key`, such as datatype and time to live, are discarded.</li>

## Return Value
Returns status string.

## Examples

You can do this as shown below.
<div class='copy separator-dollar'>
```sh
$ SET yugakey "YugaByte"
```
</div>
```sh
"OK"
```
<div class='copy separator-dollar'>
```sh
$ GET yugakey
```
</div>
```sh
"YugaByte"
```

## See Also
[`append`](../append/), [`get`](../get/), [`getrange`](../getrange/), [`getset`](../getset/), [`incr`](../incr/), [`incrby`](../incrby/), [`setrange`](../setrange/), [`strlen`](../strlen/)