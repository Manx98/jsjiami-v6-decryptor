# (实验性)基于AST的jsjiami.com代码混淆清除

### 目前支持

1. JS最牛加密-V6
    + 状态：测试通过免费版最高配置
2. SOJSON-V5版
    + 状态：测试通过免费版最高配置

### 清除效果

+ 清除字符串加密
+ 清除运算符、函数调用混淆
+ 清除无效代码块
+ 清除函数执行过程混淆

### 测试示例

* 测试文件及所在目录
    + [源码](sample/original_code.js)
    + [SOJSON-V5版_绝对不可逆配置](sample/jsjiami.com.v5_high.js)
    + [SOJSON-V5版_常规配置](sample/jsjiami.com.v5_normal.js)
    + [JS最牛加密-V6_最高配置](sample/jsjiami.com.v6_high.js)
    + [JS最牛加密-V6_常规配置](sample/jsjiami.com.v6_normal.js)
    + [JS最牛加密-V6_最高配置_解密结果](sample/jsjiami.com.v6_decrypt.js)

## 使用须知

* 解密文件中**必须**有且仅有通过JsjiamiV6或SOJSON-V5版加密的内容，且**不允许格式化**，否则将解密失败。
* 解密器会使用vm（虚拟机）执行JS中的部分代码（在一般情况下，它会被用来执行JsjiamiV6生成的解密函数）。
* 由于注释及部分变量名在代码压缩、混淆的过程中已经丢失或被篡改，此类信息无法复原。
* 如果该JS**过于复杂**或**使用了(我)不常用的语法**，可能导致解密失败，如遇到此类情况欢迎提出。
* 由于使用了AST，直接对语法树进行操作，可能导致代码与实际存在出入，只有结果仅供参考
    + 提示：结果的正确性随操作步骤叠加而逐渐降低
