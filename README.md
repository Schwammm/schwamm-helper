<div align="center">
  <img
    src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=30&pause=1500&color=3B82F6&center=true&vCenter=true&width=320&lines=schwamm-helper"
    alt="schwamm-helper"
  />
  <br>
  <img 
    src="https://placehold.co/400x400/000000/3B82F6?text=SCHWAMM%0AHELPER" 
    width="500" 
    height="500" 
    alt="SCHWAMM HELPER" 
    style="border-radius: 12px; margin-top: 15px;"
  />
</div>
<div align="center">
  <img
    src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=30&pause=1500&color=EF4444&center=true&vCenter=true&width=150&lines=1.0.8%E2%80%8B"
    alt="1.0.8"
  />
  <br>
</div>

---

Thin wrappers around Baileys APIs. **Your bot owns the socket** — this package only calls methods that exist on it.

  

```bash

npm  i  @whiskeysockets/baileys  schwamm-helper

```

  

```js

const  Helper = require('schwamm-helper');

  

await  Helper.group.demote(sock, groupJid, ['123@lid']);

await  Helper.channel.follow(sock, '123@newsletter');

await  Helper.com.leave(sock, communityJid);

await  Helper.checkuser(sock, ['name1', 'name2']);

await  Helper.checkdevice(msgId);

await  Helper.checkban('491701234567');

```

  

Prefer **`@lid`** for participant JIDs where possible.

  

---

  

## Group

  


| Method | Description |
|---|---|
| `metadata(sock, jid)` | Group metadata |
| `create(sock, name, participants?)` | Create group |
| `leave(sock, jid)` | Leave group |
| `add` / `remove` | Participants |
| `promote` / `demote` | Admins |
| `name` / `desc` | Subject, description |
| `image` / `removeImage` | Group picture |
| `mute` / `unmute` | Who can send |
| `lock` / `unlock` | Who can edit info |
| `inviteCode` / `revokeLink` | Invite link |
| `acceptInvite` / `inviteInfo` | Join via code |
| `ephemeral(sock, jid, seconds)` | Disappearing msgs (`0` = off) |
| `requests` / `approve` / `reject` | Join requests |
| `memberAddMode` / `joinApproval` | Modes |
| `all(sock)` | All participating groups |
| `kill(sock, jid, except?)` | Remove members (bot kept) |
| `takeadmin(sock, jid, except?)` | Demote admins (bot kept) |


  

```js

await  Helper.group.add(sock, gid, ['123@lid']);

await  Helper.group.kill(sock, gid, [...owners, 'admins']);

await  Helper.group.takeadmin(sock, gid, owners);

```

  

`kill` always keeps the bot and the owner. `'admins'` in `except` keeps every admin.

  

---

  

## Channel

  

| Method | Description |
|---|---|
| `create(sock, name, desc?)` | Create channel |
| `metadata(sock, key, type?)` | Metadata (`jid` \| `invite`) |
| `subscribers(sock, jid)` | Subscriber info |
| `follow` / `unfollow` | Subscription |
| `mute` / `unmute` | Your notifications |
| `name` / `desc` | Title, description |
| `image` / `removeImage` | Picture |
| `delete(sock, jid)` | Delete channel |
| `demote` / `changeOwner` | Admins / ownership |
| `react(sock, jid, serverId, emoji)` | React to message |
| `messages(sock, jid, count?, since?, after?)` | Fetch messages |
| `adminCount(sock, jid)` | Admin count |
| `send(sock, jid, content, options?)` | Post a message |


  

```js

await  Helper.channel.follow(sock, '123@newsletter');

await  Helper.channel.send(sock, '123@newsletter', { text:  'Hello'  });

```

  

---

  

## Com

  


| Method | Description |
|---|---|
| `metadata` / `create` / `leave` | Basics |
| `createGroup` / `link` / `unlink` / `linked` | Subgroups |
| `add` / `remove` / `promote` / `demote` | Participants |
| `name` / `desc` / `image` / `removeImage` | Info |
| `mute` / `unmute` / `lock` / `unlock` | Settings |
| `inviteCode` / `revokeLink` / `acceptInvite` / `inviteInfo` | Invites |
| `ephemeral` / `requests` / `approve` / `reject` | Extra |
| `memberAddMode` / `joinApproval` | Modes |
| `all(sock)` | All communities |
| `kill(sock, jid, except?)` | Same rules as `group.kill` |
| `takeadmin(sock, jid, except?)` | Demote admins (bot kept) |

  

```js

await  Helper.com.kill(sock, comJid, [...owners, 'admins']);

await  Helper.com.takeadmin(sock, comJid, owners);

```

  

---

  

## Checks

  
  

| Method | Description |
|---|---|
| `checkuser(sock, usernames)` | Username free or taken. String, array, or comma-separated. |
| `checkdevice(msgId)` | Device from a message ID (`iOS`, `WhatsApp Web`, `Android`). |
| `checkban(number)` | Ban check. Returns the API payload. |

  

```js

const  rows = await  Helper.checkuser(sock, 'user1, user2');

const  info = Helper.checkdevice(stanzaId);

const  data = await  Helper.checkban('491701234567');

```

  

---

  

## License

  

MIT