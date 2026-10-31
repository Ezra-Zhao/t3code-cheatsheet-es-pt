# 手机遥控演练 | Phone remote-control setup drill

把「出门也能盯本机 agent」这条链路一次打通，顺序别乱：

1. 本机先单练：挑一个 provider 装好 CLI 并登录（如 `claude auth login`），在终端里单独派一个小任务，确认 agent 本身没问题。
2. 装 T3 Code：`curl -fsSL https://t3.codes/install.sh | sh` 后跑 `t3`，在本机网页版里确认会话可见、能派活、权限弹窗能批能拒。
3. 设权限模式：打开上游仓 docs/ 里的 Permission modes 那篇，按「远程时收紧」配好，再考虑开远程——不要先开远程后补权限。
4. 连手机：装 iOS/Android App，按 docs/ 的 Remote access 说明与本机服务配对；用手机批一次权限、派一个小任务，走通全程。
5. 转常驻并验断线：`t3 service install` 后合上笔记本试一次远程连接，确认机器睡眠设置不会把长任务掐断，再放心出门跑长任务。
