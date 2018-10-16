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

## 备注:

#### 角色属性key

血量 = Hp

饱腹值 = FoodDegree 

~~~~~~
DbTableFieldName.Character = {--属性相关(包括生存属性和战斗属性.其中战斗属性暂时不保存)
	--基础属性
	HEALTH_POINT			= "Hp",					--生命值
	MAX_HEALTH_POINT		= "MaxHp",				--生命值上限
	--维生值属性,越高越好
	FOOD_DEGREE				= "FoodDegree",			--饱腹值.默认100
	DRINK_DEGREE			= "DrinkDegree",		--饮水值.默认100
	MIND_DEGREE				= "MindDegree",			--神志值.默认100
	--压力值属性,越低越好
	URINE_DEGREE			= "UrineDegree",		--便溺值
	DIRTY_DEGREE			= "DirtyDegree",		--不洁值
	SICK_DEGREE				= "SickDegree",			--疫病值
	--耐力相关
	VIT						= "Vit",				--耐力,冲刺/蓄力等使用
	VIT_MAX					= "VitMax",				--耐力上限

	--天赋相关
	CUR_PLAN_ID				= "CurPlanId",			--当前天赋方案Id<number>,
	MAX_PLAN_ID				= "MaxPlanId",			--最大天赋方案Id<number>,
	TOTAL_TALENT			= "TotalTalent",		--总天赋点数<number>,
	TALENT_FROM_ITEM		= "TalentFromItem",		--道具提供的天赋点数<number>,
	TALENT_ITEM_COUNT		= "TalentItemCount",	--已使用天赋道具次数<number>,

	--以下待定
	--属性更新时间戳
	ATTR_UPDATE_TIME		= "AttrUpdateTime",		--属性更新时间戳,客户端需求数据更新时根据该值去计算相关属性变化
	--状态
	CHARACTER_STATE			= "CharaState",			--角色状态及计数
	--Buff列表
	BUFF_LIST				= "BuffList",			--角色Buff列表
}
~~~~~~

