## 快速登录流程

### 流程图

```flow
s=>start: 初始化
e=>end: 进入游戏
getLoginServerStatus=>operation: 获取登录服务器状态
isLoginServerStatusOk=>condition: 检查登录服务器状态
showTipsTheLoginServerIsMaintain=>operation: 登录服务器维护中
clickOutsideOfTheDlgToExitApp=>operation: 点任意区域退出app
showSDKLoginDlg=>operation: 显示SDK登录界面
inputUserNameAndPassword=>operation: 在SDK登录对话框中输入用户名和密码
getLoginToken=>operation: 获取登录token
sendTokenToLoginServer=>operation: 发送登录token给服务端
isLoginTokenOk=>condition: 服务端验证token是否正确
getGameServerStatus=>operation: 获取区服状态
isGameServerMaintain=>condition: 区服维护中
noHandle=>operation: 未处理
showSelectGameServer=>operation: 显示选服界面
getRoleInfo=>operation: 获取角色信息
checkHaveRoleInfo=>condition: 是否有角色信息
showEnterGameDlg=>operation: 显示进行游戏界面


s->getLoginServerStatus->isLoginServerStatusOk
isLoginServerStatusOk(no)->showTipsTheLoginServerIsMaintain
isLoginServerStatusOk(yes)->showSDKLoginDlg->getLoginToken->sendTokenToLoginServer->isLoginTokenOk
isLoginTokenOk(no)->noHandle
isLoginTokenOk(yes)->showEnterGameDlg

```


