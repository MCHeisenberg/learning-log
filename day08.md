### 1 开始整理、规范化目前学到的所有知识、代码格式结构

- （1）创建新包day08，双向死斗小游戏规范化，代码正规军化。
- （2）`getDamage()` 改成 `takeDamage()`
- 新增 判断伤害是不是正数
- 新增 判断造成伤害后 `hp`是否下溢，是则修正为0 
- 新增 造成伤害后提示:`xx受到了xx伤害`
-  （3）`machineGun()`中新增
- 先输出提示：`使用【动能机枪】！`
- （4）`orbitalStrike()`调整：
- 优化提示：`能量不足` --> `能量不足，无法发动【轨道天基武器】`
- 先判断能量值，不足则直接`return`，不扣能量
- 使用技能提示`使用【轨道天基武器】`
- （5）优化`repair()`
- 同样判断能量值并提示（+`return`）
- 注意`hp`恢复后不能超过`maxHp`
- （6）技能释放的主语可以加在输出语句中（带上名字属性`name`）
- （7）代码输出和方法调用的细节顺序可以细致一点

### 2 把main变薄

把while里面的

把显示菜单       ;     战况拉出去;

mecha的技能释放拉出去     ;   把tyrant的反击也拉出去   

分别单独成一个方法

while外面再来个显示结果的方法

然后sc.close()

### 3 判断输入choice时合不合规

`sc.hasNextInt()`输入的是不是int

```java
public static int getValidChioce(){
    while(true){
        if(!sc.hasNextInt){
            System.out.println("输入错误，请输入：1、2 或 3 请重新输入：");
            sc.next;
            continue;
        }
        
        if(sc.nextInt >=1 && sc.nextInt <=3){
            return sc.nextInt;
        }

        System.out.println("输入错误，请输入：1、2 或 3，请重新输入：");
    }
}


```



### 2 总结

- （1）凡是消化`energy`的方法，
- 先判断`energy`值，
- 不足就输出提示
- 并直接`return`
- 不扣`energy`
- （2）使用技能时给提示
- （3）属性值边界。
- 增长的上限。`hp = maxHp`
- 减少不溢出下限。`hp = 0`
- （4）方法的参数**被使用前**可能需要**先判断正负**
- `takeDamage(int damage)`里`damage`不能是负数，不然就成加血了

## 3 Mistakes

- （1）`main`方法中`myMecha.orbitalStrike()`  --> `myMecha.orbitalStrike(tyrant)`
- （2）`repair()`里面血量差的算式写反了。
- （3）`System.out.println("请重新输入：");`-->`System.out.print("请重新输入：");`