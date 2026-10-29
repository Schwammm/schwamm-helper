<div align="center">
  <img
    src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=35&pause=1500&color=3B82F6&center=true&vCenter=true&width=320&lines=SCHWAMM-HELPER"
    alt="schwamm-helper"
  />
  <br>
  <img 
    src="https://placehold.co/500x500/000000/3B82F6?text=SCHWAMM%0AHELPER&font=fira-code" 
    width="500" 
    height="500" 
    alt="SCHWAMM HELPER" 
    style="border-radius: 12px; margin-top: 15px;"
  />
</div>

<div align="center">
  <img
    src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=30&pause=1500&color=3B82F6&center=true&vCenter=true&width=150&lines=1.1.0%E2%80%8B"
    alt="1.1.0"
  />
</div>

<p align="center">
  <a href="https://www.npmjs.com/package/schwamm-helper">
    <img src="https://img.shields.io/badge/npm-schwamm--helper-3B82F6?labelColor=000000&style=for-the-badge&logo=npm&logoColor=white" alt="npm">
  </a>
  <a href="https://github.com/Schwammm/schwamm-helper">
    <img src="https://img.shields.io/badge/GitHub-schwamm--helper-3B82F6?labelColor=000000&style=for-the-badge&logo=github&logoColor=white" alt="GitHub">
  </a>
</p>

<p align="center">
  <img src="https://img.shields.io/npm/dt/schwamm-helper?color=3B82F6&labelColor=000000&style=for-the-badge" alt="total downloads">
  <img src="https://img.shields.io/badge/license-MIT-3B82F6?labelColor=000000&style=for-the-badge" alt="license">
</p>

<p align="center"><i>Thin wrappers around Baileys APIs — your bot owns the socket.</i></p>

  

```bash

npm  i  @whiskeysockets/baileys  schwamm-helper

```

---

## Changelog

### 1.1.0
- updated full README

## Table of Contents

- [Group](#group)
- [Channel](#channel)
- [Com](#com)
- [Checks](#checks)
- [License](#license)

---

## Group

<details>
<summary><b>metadata</b></summary>

```js
const meta = await Helper.group.metadata(sock, groupJid);
```

</details>

<details>
<summary><b>create</b></summary>

```js
const group = await Helper.group.create(sock, 'My Group', ['123@lid']);
```

</details>

<details>
<summary><b>leave</b></summary>

```js
await Helper.group.leave(sock, groupJid);
```

</details>

<details>
<summary><b>add</b></summary>

```js
await Helper.group.add(sock, gid, ['123@lid']);
```

</details>

<details>
<summary><b>remove</b></summary>

```js
await Helper.group.remove(sock, gid, ['123@lid']);
```

</details>

<details>
<summary><b>promote</b></summary>

```js
await Helper.group.promote(sock, gid, ['123@lid']);
```

</details>

<details>
<summary><b>demote</b></summary>

```js
await Helper.group.demote(sock, gid, ['123@lid']);
```

</details>

<details>
<summary><b>name</b></summary>

```js
await Helper.group.name(sock, gid, 'New Subject');
```

</details>

<details>
<summary><b>desc</b></summary>

```js
await Helper.group.desc(sock, gid, 'New description');
```

</details>

<details>
<summary><b>image</b></summary>

```js
await Helper.group.image(sock, gid, 'https://…/pic.jpg');
```

</details>

<details>
<summary><b>removeImage</b></summary>

```js
await Helper.group.removeImage(sock, gid);
```

</details>

<details>
<summary><b>mute</b></summary>

```js
await Helper.group.mute(sock, gid);
```

</details>

<details>
<summary><b>unmute</b></summary>

```js
await Helper.group.unmute(sock, gid);
```

</details>

<details>
<summary><b>lock</b></summary>

```js
await Helper.group.lock(sock, gid);
```

</details>

<details>
<summary><b>unlock</b></summary>

```js
await Helper.group.unlock(sock, gid);
```

</details>

<details>
<summary><b>inviteCode</b></summary>

```js
const code = await Helper.group.inviteCode(sock, gid);
```

</details>

<details>
<summary><b>revokeLink</b></summary>

```js
await Helper.group.revokeLink(sock, gid);
```

</details>

<details>
<summary><b>acceptInvite</b></summary>

```js
await Helper.group.acceptInvite(sock, 'INVITECODE');
```

</details>

<details>
<summary><b>inviteInfo</b></summary>

```js
const info = await Helper.group.inviteInfo(sock, 'INVITECODE');
```

</details>

<details>
<summary><b>ephemeral</b></summary>

```js
await Helper.group.ephemeral(sock, gid, 86400); // 0 = off
```

</details>

<details>
<summary><b>requests</b></summary>

```js
const reqs = await Helper.group.requests(sock, gid);
```

</details>

<details>
<summary><b>approve</b></summary>

```js
await Helper.group.approve(sock, gid, ['123@lid']);
```

</details>

<details>
<summary><b>reject</b></summary>

```js
await Helper.group.reject(sock, gid, ['123@lid']);
```

</details>

<details>
<summary><b>memberAddMode</b></summary>

```js
await Helper.group.memberAddMode(sock, gid, 'all_member_add');
```

</details>

<details>
<summary><b>joinApproval</b></summary>

```js
await Helper.group.joinApproval(sock, gid, true);
```

</details>

<details>
<summary><b>all</b></summary>

```js
const groups = await Helper.group.all(sock);
```

</details>

<details>
<summary><b>kill</b></summary>

```js
await Helper.group.kill(sock, gid, [...owners, 'admins']);
```

`kill` always keeps the bot and the owner. `'admins'` in `except` keeps every admin.

</details>

<details>
<summary><b>takeadmin</b></summary>

```js
await Helper.group.takeadmin(sock, gid, owners);
```

</details>

---

## Channel

<details>
<summary><b>create</b></summary>

```js
const ch = await Helper.channel.create(sock, 'My Channel', 'Description');
```

</details>

<details>
<summary><b>metadata</b></summary>

```js
const meta = await Helper.channel.metadata(sock, '123@newsletter', 'jid');
```

</details>

<details>
<summary><b>subscribers</b></summary>

```js
const subs = await Helper.channel.subscribers(sock, chJid);
```

</details>

<details>
<summary><b>follow</b></summary>

```js
await Helper.channel.follow(sock, '123@newsletter');
```

</details>

<details>
<summary><b>unfollow</b></summary>

```js
await Helper.channel.unfollow(sock, '123@newsletter');
```

</details>

<details>
<summary><b>mute</b></summary>

```js
await Helper.channel.mute(sock, chJid);
```

</details>

<details>
<summary><b>unmute</b></summary>

```js
await Helper.channel.unmute(sock, chJid);
```

</details>

<details>
<summary><b>name</b></summary>

```js
await Helper.channel.name(sock, chJid, 'New Title');
```

</details>

<details>
<summary><b>desc</b></summary>

```js
await Helper.channel.desc(sock, chJid, 'New description');
```

</details>

<details>
<summary><b>image</b></summary>

```js
await Helper.channel.image(sock, chJid, 'https://…/pic.jpg');
```

</details>

<details>
<summary><b>removeImage</b></summary>

```js
await Helper.channel.removeImage(sock, chJid);
```

</details>

<details>
<summary><b>delete</b></summary>

```js
await Helper.channel.delete(sock, chJid);
```

</details>

<details>
<summary><b>demote</b></summary>

```js
await Helper.channel.demote(sock, chJid, ['123@lid']);
```

</details>

<details>
<summary><b>changeOwner</b></summary>

```js
await Helper.channel.changeOwner(sock, chJid, '456@lid');
```

</details>

<details>
<summary><b>react</b></summary>

```js
await Helper.channel.react(sock, chJid, serverId, '👍');
```

</details>

<details>
<summary><b>messages</b></summary>

```js
const msgs = await Helper.channel.messages(sock, chJid, 20);
```

</details>

<details>
<summary><b>adminCount</b></summary>

```js
const n = await Helper.channel.adminCount(sock, chJid);
```

</details>

<details>
<summary><b>send</b></summary>

```js
await Helper.channel.send(sock, '123@newsletter', { text: 'Hello' });
```

</details>

---

## Com

<details>
<summary><b>metadata</b></summary>

```js
const meta = await Helper.com.metadata(sock, comJid);
```

</details>

<details>
<summary><b>create</b></summary>

```js
const com = await Helper.com.create(sock, 'My Community');
```

</details>

<details>
<summary><b>leave</b></summary>

```js
await Helper.com.leave(sock, comJid);
```

</details>

<details>
<summary><b>createGroup</b></summary>

```js
await Helper.com.createGroup(sock, comJid, 'Subgroup');
```

</details>

<details>
<summary><b>link</b></summary>

```js
await Helper.com.link(sock, comJid, groupJid);
```

</details>

<details>
<summary><b>unlink</b></summary>

```js
await Helper.com.unlink(sock, comJid, groupJid);
```

</details>

<details>
<summary><b>linked</b></summary>

```js
const groups = await Helper.com.linked(sock, comJid);
```

</details>

<details>
<summary><b>add</b></summary>

```js
await Helper.com.add(sock, comJid, ['123@lid']);
```

</details>

<details>
<summary><b>remove</b></summary>

```js
await Helper.com.remove(sock, comJid, ['123@lid']);
```

</details>

<details>
<summary><b>promote</b></summary>

```js
await Helper.com.promote(sock, comJid, ['123@lid']);
```

</details>

<details>
<summary><b>demote</b></summary>

```js
await Helper.com.demote(sock, comJid, ['123@lid']);
```

</details>

<details>
<summary><b>name</b></summary>

```js
await Helper.com.name(sock, comJid, 'New Name');
```

</details>

<details>
<summary><b>desc</b></summary>

```js
await Helper.com.desc(sock, comJid, 'New description');
```

</details>

<details>
<summary><b>image</b></summary>

```js
await Helper.com.image(sock, comJid, 'https://…/pic.jpg');
```

</details>

<details>
<summary><b>removeImage</b></summary>

```js
await Helper.com.removeImage(sock, comJid);
```

</details>

<details>
<summary><b>mute</b></summary>

```js
await Helper.com.mute(sock, comJid);
```

</details>

<details>
<summary><b>unmute</b></summary>

```js
await Helper.com.unmute(sock, comJid);
```

</details>

<details>
<summary><b>lock</b></summary>

```js
await Helper.com.lock(sock, comJid);
```

</details>

<details>
<summary><b>unlock</b></summary>

```js
await Helper.com.unlock(sock, comJid);
```

</details>

<details>
<summary><b>inviteCode</b></summary>

```js
const code = await Helper.com.inviteCode(sock, comJid);
```

</details>

<details>
<summary><b>revokeLink</b></summary>

```js
await Helper.com.revokeLink(sock, comJid);
```

</details>

<details>
<summary><b>acceptInvite</b></summary>

```js
await Helper.com.acceptInvite(sock, 'INVITECODE');
```

</details>

<details>
<summary><b>inviteInfo</b></summary>

```js
const info = await Helper.com.inviteInfo(sock, 'INVITECODE');
```

</details>

<details>
<summary><b>ephemeral</b></summary>

```js
await Helper.com.ephemeral(sock, comJid, 86400);
```

</details>

<details>
<summary><b>requests</b></summary>

```js
const reqs = await Helper.com.requests(sock, comJid);
```

</details>

<details>
<summary><b>approve</b></summary>

```js
await Helper.com.approve(sock, comJid, ['123@lid']);
```

</details>

<details>
<summary><b>reject</b></summary>

```js
await Helper.com.reject(sock, comJid, ['123@lid']);
```

</details>

<details>
<summary><b>memberAddMode</b></summary>

```js
await Helper.com.memberAddMode(sock, comJid, 'all_member_add');
```

</details>

<details>
<summary><b>joinApproval</b></summary>

```js
await Helper.com.joinApproval(sock, comJid, true);
```

</details>

<details>
<summary><b>all</b></summary>

```js
const coms = await Helper.com.all(sock);
```

</details>

<details>
<summary><b>kill</b></summary>

```js
await Helper.com.kill(sock, comJid, [...owners, 'admins']);
```

Same rules as `group.kill`.

</details>

<details>
<summary><b>takeadmin</b></summary>

```js
await Helper.com.takeadmin(sock, comJid, owners);
```

</details>

---

## Checks

<details>
<summary><b>checkuser</b></summary>

String, array, or comma-separated.

```js
const rows = await Helper.checkuser(sock, 'user1, user2');
```

</details>

<details>
<summary><b>checkdevice</b></summary>

Returns e.g. `iOS`, `WhatsApp Web`, `Android`.

```js
const info = Helper.checkdevice(stanzaId);
```

</details>

<details>
<summary><b>checkban</b></summary>

Returns the API payload.

```js
const data = await Helper.checkban('491701234567');
```

</details>

---


<p  align="center">
<strong>MADE BY SCHWAMM</strong>
</p>

## License

MIT