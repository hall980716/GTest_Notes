# GTest_Notes

Google Test 是谷歌开发并维护的测试C++框架

测试方法：
单元测试 - 以函数、类为单位进行独立测试
集成测试 - 多个组件组合起来进行测试
黑盒测试 - 不关注代码内部逻辑，只关注功能的测试
白盒测试 - 需要关注代码内部逻辑的测试，单元测试属于白盒测试
验收测试 - 交付给用户之前的测试，符合用户需求

ASSERT 与 EXPECT 区别：ASSERT 出错会停止运行，而 EXPECT 出错会继续执行后续逻辑
常见如（ASSERT_EQ ASSERT_NE ASSERT_GT ASSERT_LT(val1, val2)），(EXPECT_TRUE EXPECT_FALSE(condition))

XX_STREQ XX_STRNE(str1, str2) 不区分大小写对比字符串
XX_STRCASEEQ XX_STRCASENE(str1, str2) 区分大小写对比字符串

支持参数化测试 - 一次性运行多组测试用例（需要派生自testing::TestWithParam）TEST_P

Test Fixture（测试夹具）用于在相似环境下运行多个测试用例（需要继承于testing::test）TEST_F
测试夹具：①继承自testing::test；②类内定义Setup() 与 Teardown() 所要做的事；③在TEST_F内相当于在Setup()与Teardown()之间的环境下进行的测试。

Google Mock - 用于伪造已有的或模拟不存在的对象，允许在不执行实际的对象函数情况下测试类的方法
MOCK_METHODx()，代表模拟一个接收x个参数的函数
ON_CALL：设置模拟对象的预期行为
DoDefault：用在WillOnce宏后，说明该测试返回模拟函数的默认值
DoALL：用于指定多个动作按顺序执行，并且最后期待返回一个特定的值
testing::Invoke：在模拟方法中执行自定义函数
