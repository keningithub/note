# 临近提示配置说明

## 触发条件

#### 任务相关

- 任务接收  {"t":"mission", missionId":1, "event":"recv"}
- 任务完成  {"t":"mission", "missionId":1, "event":"comp"}

#### 角色属性相关

- 血量上升 {"t":"player", "attr":"Hp", "event":"up", "val":90}
- 饥饿度下降 {"t":"player", "attr":"FoodDegree", "event":"down", "val":20}
- 饥渴度下降 {"t":"player", "attr":"DrinkDegree", "event":"down", "val":20}

#### 道具相关

- 道具获取 {"t":"item", "itemId":30001, "event":"add", "count":1}

#### 耐久度相关

- 耐久度下降 {"t":"durable", "storeKey":"1_2", "event":"down", "val":20}

  storeKey: storeId_storeIndex

#### 身上物品数量相关

- 拥有指定物品数量达到指定数量 {"t":"carry",  "items":{"1001":20, "1002":10}}

#### 基础属性相关

- 等级达到指定值 {"t":"base", "attr":"Level", "event":"up", "val":4}
- 体力达到指定值 {"t":"base", "attr":"Strength", "event":"down", "val":20}

#### 据点相关

- 出现指定据点 {"t":"point", "pointId":1001}

#### 游戏时间
- 当前游戏时间跨越指定时间点 {"t":"gametime", "time":201200, "points":[100, 1101]} 

  time为天天时时分分的格式, 即191200为第20天的12:00

#### 游戏时段
- 当游戏时间在指定时间段内时触发一次 {"t":"gametimebucket", "time":201200, "points":[100, 1101]} 

  time为天天时时分分的格式, 即191200为第20天的12:00

#### 使用物品或挂载装备时
- 角色使用指定物品时 {"t":"useitem", "itemId":30001}

#### Entity属性相关

- 燃料下降 {"t":"entity", "entityId":"CurVehicle", "attr":"Vit", "event":"down", "val":0}




## 附加条件

#### 待协商
- [{"key":"Hp", "val":20, "cpr":"lt/gt/le/ge"}]

  lt: 小于

  gt: 大于

  le: 小于等于

  lg: 大于等于

  注: 不写cpr时, 判断相等

## 备注:

#### 角色属性attr

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



#### storeKey

storeKey: storeId_storeIndex

主武器: storeKey: 2_1

``````
ItemDef.StoreType = {
	--前面这些类型与玩家自身的容器编号对应
	STORE_PACKAGE		= 1,	--玩家身上背包(口袋+背包)
	STORE_EQUIP			= 2,	--装备栏 <--------------------------
	STORE_PACKAGE_GRID	= 3,	--放背包的格子
	STORE_FURNITURE		= 4,	--家具栏
	STORE_VEHICLE		= 5,	--载具栏
	STORE_ROBOT			= 6,	--天赋无人机
	--20000起表示当前map对应的容器Id(尸体,宝箱)
	STORE_MAP_START		= 20000,
}

ItemDef.EquipPos = {
	--装备栏位置
	MAIN_WEAPON			= 1,		--主武器 <--------------------------
	SUB_WEAPON			= 2,		--副武器
	PROJECTILE_WEAPON	= 3,		--投掷武器
	HEAD				= 4,		--头部
	CHEST				= 5,		--胸部
	HAND				= 6,		--手部
	LEG					= 7,		--腿部
	FOOT				= 8,		--脚部
}
``````

