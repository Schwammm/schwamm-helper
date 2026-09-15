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
    src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=30&pause=1500&color=EF4444&center=true&vCenter=true&width=150&lines=1.0.5%E2%80%8B"
    alt="1.0.5"
  />
  <br>
</div>

---

Thin wrappers around Baileys APIs. **Your bot owns the socket** — this package only calls methods that exist on it.

```bash
npm i @whiskeysockets/baileys schwamm-helper
```

```js
const Helper = require('schwamm-helper');

await Helper.group.demote(sock, groupJid, ['123@lid']);
await Helper.channel.follow(sock, '123@newsletter');
await Helper.com.leave(sock, communityJid);
await Helper.account.setStatus(sock, 'Hello');
await Helper.chat.archive(sock, chatJid);
```

Prefer **`@lid`** for participant JIDs where possible.

If a method is missing on your Baileys build:

```text
schwamm-helper: sock.<method> is not available on this Baileys build
```

---

## Group — `Helper.group`

| Method | Description |
| --- | --- |
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
await Helper.group.add(sock, gid, ['123@lid']);
await Helper.group.name(sock, gid, 'New title');
await Helper.group.mute(sock, gid);
await Helper.group.revokeLink(sock, gid);
await Helper.group.ephemeral(sock, gid, 86400);
await Helper.group.removeImage(sock, gid);
```

### `kill`

Removes everyone **except**:

- the bot (always)
- JIDs in `except` (prefer `@lid`)
- all admins, if `except` includes `'admins'`

```js
const owners = JSON.parse(fs.readFileSync('owners.json', 'utf8')).map((o) => o.jid);

await Helper.group.kill(sock, gid);
await Helper.group.kill(sock, gid, owners);
await Helper.group.kill(sock, gid, [...owners, 'admins']);
```

### `takeadmin`

Demotes every admin **except** the bot and JIDs in `except`.

```js
await Helper.group.takeadmin(sock, gid);
await Helper.group.takeadmin(sock, gid, owners);
```

---

## Channel — `Helper.channel`

Maps to Baileys `newsletter*` (WhatsApp Channels).

| Method | Description |
| --- | --- |
| `create(sock, name, desc?)` | Create channel |
| `metadata(sock, key, type?)` | Metadata (`jid` \| `invite`) |
| `subscribers(sock, jid)` | Subscriber info |
| `follow` / `unfollow` | Subscription |
| `mute` / `unmute` | **Your** notifications |
| `name` / `desc` | Title, description |
| `image` / `removeImage` | Picture |
| `delete(sock, jid)` | Delete channel |
| `demote` / `changeOwner` | Admins / ownership |
| `react(sock, jid, serverId, emoji)` | React to message |
| `messages(sock, jid, count?, since?, after?)` | Fetch messages |
| `adminCount(sock, jid)` | Admin count |

```js
await Helper.channel.follow(sock, '123@newsletter');
await Helper.channel.mute(sock, '123@newsletter');
await Helper.channel.name(sock, '123@newsletter', 'News');
await Helper.channel.delete(sock, '123@newsletter');
```

> `channel.mute` only changes **your** notification state. For group send permissions use `group.mute` / `group.unmute`.

---

## Community — `Helper.com`

Needs Baileys with `community*` methods (e.g. v7.x).

| Method | Description |
| --- | --- |
| `metadata` / `create` / `leave` | Basics |
| `createGroup` / `link` / `unlink` / `linked` | Subgroups |
| `add` / `remove` / `promote` / `demote` | Participants |
| `name` / `desc` / `image` | Info |
| `mute` / `unmute` / `lock` / `unlock` | Settings |
| `inviteCode` / `revokeLink` / `acceptInvite` / `inviteInfo` | Invites |
| `ephemeral` / `requests` / `approve` / `reject` | Extra |
| `memberAddMode` / `joinApproval` | Modes |
| `all(sock)` | All communities |
| `kill(sock, jid, except?)` | Same rules as `group.kill` |

```js
await Helper.com.name(sock, comJid, 'Our Community');
await Helper.com.desc(sock, comJid, 'Welcome');
await Helper.com.kill(sock, comJid, [...owners, 'admins']);
```

---

## Account — `Helper.account`

| Method | Description |
| --- | --- |
| `picture(sock, jid?, type?)` | Profile picture URL |
| `setPicture(sock, media)` | Set own picture |
| `removePicture(sock)` | Remove own picture |
| `status(sock, jid?)` | Fetch about |
| `setStatus(sock, text)` | Set about |
| `setName(sock, name)` | Push name |
| `blockList` / `block` / `unblock` | Blocklist |
| `privacy(sock)` | Privacy settings |

```js
await Helper.account.setStatus(sock, 'Schwamm');
await Helper.account.setName(sock, 'Schwamm Bot');
await Helper.account.block(sock, '123@lid');
await Helper.account.blockList(sock);
```

---

## Chat — `Helper.chat`

| Method | Description |
| --- | --- |
| `archive` / `unarchive` | Archive |
| `pin` / `unpin` | Pin |
| `mute(sock, jid, durationMs?)` | Mute notifications |
| `unmute(sock, jid)` | Unmute |
| `star` / `unstar` | Star messages |

```js
await Helper.chat.archive(sock, jid);
await Helper.chat.pin(sock, jid);
await Helper.chat.mute(sock, jid, 8 * 60 * 60 * 1000);
await Helper.chat.unmute(sock, jid);
```

---

## License

MIT