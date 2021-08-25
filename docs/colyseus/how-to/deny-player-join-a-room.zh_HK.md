您可以在调用 {1>onAuth()<1} 或 {2>onJoin()<2} 方法时展示一个错误提示来拒绝玩家接入。

至于何时执行拒绝操作则取决于您的用例。

下方是验证 {1>@colyseus/social<1} 身份认证令牌，以及检索与用户 id 关联的 {2>Hero<2} 记录。

\`\`typescript export class BattleRoom extends Room {

  onCreate(options) { this.levelRequired = 10; }

  async onAuth(client, options) { const userId = verifyToken(options.token).\_id; const hero = await Hero.findOne({ userId });

    if (!hero) {
      throw new Error("'Hero' not found in the database!");

    } else if (hero.level < this.levelRequired) {
      throw new Error("player do not have the level required to be on this room.");

    }

    return hero;
  }

} \`\`\`

客户端在尝试加入房间时会收错误提示：

{1>typescript client.joinOrCreate("battle", {}).then(room => { // ... }).catch(e => { console.log(e) // "'Hero' not found in the database!" }) <1}