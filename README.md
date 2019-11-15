# WORK-LOAD BALANCE 

Contributors:

Guanglei Wang(Fei Ma) 

Huiqiang Mao(Mo Xun)

## 数据

### 必要内容

1. 网络拓扑结构（TREE， STORE to SHOPS， 每个店包含的SKU）[srcWarehouseMap, dstWarehouseMap, tree]
2. 计划周期 （T, 4~7 Day), 目标在架率 (e.g., 0.95)
3. 历史销量 （在架约束）stockMap
4. 期初可用库存   （FOR SKU， SHOP， 相应的KPSACK 约束）
5. 出库能力   
6. 箱规约束
7. 惩罚项参数 （W （TURNOVER）， BETA（SKU 在架总数）， ALPHA （折扣系数 0.8~0.9）， GAMMA （能力弹性系数，20%））

### 数据结构

1. STORE （store_id, SKU， 出库能力，期初库存， BIZDATE）(WarehouseInfoDTO)
2. SHOP  （shop_id, SKU， 库存水位， 销量，BIZDATE）--(WarehouseInfoDTO)
3. SKU  （sku_id, SHOP, 箱规格， 价格）
4. 常数项：计划周期， 惩罚项目参数， 


### D2 表格式

参照上述数据结构

1. STORE (store_id, sku_id, outbound_ability, init_inventory, bizdate, ds)
2. SHOP (shop_id, sku_id, inventory, sales, bizdate, ds)
3. SKU (shop_id, sku_id, price, delivery_spec, ds)


### 目标
最小化周转
# easyOpt
