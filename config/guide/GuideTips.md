# 临近提示配置说明

## 任务相关

- 任务接收  [{"t":"mission", missionId":1, "event":"received"}]
- 任务完成  [{"t":"mission", "missionId":1, "event":"completed"}]

## 角色属性相关

- 血量上升 [{"t":"player", "attr":"hp", "event":"up", "val":90}]
- 饥饿度下降 [{"t":"player", "attr":"food", "event":"down", "val":20}]
- 饥渴度下降 [{"t":"player", "attr":"drink", "event":"down", "val":20}]

## 道具相关

- 道具获取 [{"t":"item", itemId":30001, "event":"add", "count":1}]

