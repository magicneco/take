# take
报错的原因是栈溢出。
是由于使用Jpa查询时产生了死循环或无限递归。
在接口写完后，测试时，就发现 StackOverflowError ，然后一调试就发现了问题，遇到一个多对多的关系，就引出了递归调用+死循环 ，所以在查询的时候一定要注意这个问题，当表的字段和数据量较小时，很难发现
在遍历集合时，
for（Role role : user.getRoleList()）{
        System.out.println(role);
}
输出一个role对象时，也会输出userlist,因为是双向关联的，所以也会触发user对象，接下来便是roleList。。。产生无限递归，导致栈溢出。
