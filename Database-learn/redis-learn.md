Redis数据类型

Normal commands

字符串【String】
使用场景：缓存、计数器、分布式锁等
set key value
mset key0 value0 key1 vaule1 ...
get key
mget key0 key1 key2 ...
# key 已经存在则改变其值
set key value
# 该值 seconds 秒后过期
setex key seconds value  
# 得到就值设置新值
getset key key value
# 获得该键的字符串长度
strlen key 
# 追加字符串
append key value



哈希【Hash】
使用场景：存储具有一定结构化的数据
hset key filed1 value1 filed2 vaule2 ...
hget key filed1
hdel key filed1 
# 判断key的field是否存在
hexists key filed
# 获取指定key的filed数量【内部计数，生成环境可用】
hlen key
# 批量获得hash的field对应的value
hmget key field [field …]	
# 批量设置hash的field和value
hmset key field value [field1 value1 ...]	
# 获取key对应所有field和value【生成环境慎用】
HGETALL key	
# 返回key对应的所有value【生成环境慎用】
HVALS key	
# 返回key对应的所有field【生成环境慎用】
HKEYS key	
# 不存在此key对应的field则设置
HSETNX key field value	


列表【List】
列表为有序、可重复结构。可指定位置插入和删除、也可从左右插入和弹出（模拟栈结构）
# 从列表的(左|右)插入元素
LPUSH|RPUSH key value [value …]	
# 在list指定的值前|后插入新元素【时间复杂度O(N)】
LINSERT key BEFORE|AFTER value newValue	
# 从列表左侧|右侧弹出一个元素
LPOP|RPOP key	
# 根据count值，从列表删除所有等于value的值【时间复杂度O(N)】
# 【count>0，从左到右删除count个】
# 【count<0，从右到坐删除count个】
# 【count=0，删除所有value相等的值】
LREM key count value	
# 按照索引范围保留list，删除大链表有用【时间复杂度O(N)】
LTRIM key start end	
# 获取列表指定索引范围内的值，数值为负则从右往左取值【时间复杂度O(N)】
LRANGR key start end	
# 获取列表指定索引的值，数值为负则从右取值【时间复杂度O(N)】
LINDEX key index	
# 获取list长度【内部计数，生成环境可用】
LLEN key
# 设置指定位置的值【时间复杂度O(N)】
LSET key index newValue	
# LPOP/RPOP的阻塞版，timeout为0则表示永不阻塞
BLPOP|RLPOP key timeout	

使用技巧：

LPUSH + LPOP = Stack
LPUSH + RPOP = Queue
LPUSH + LTRIM = Capped Collection【固定容量集合】
LPUSH + BRPOP = Block Queue

