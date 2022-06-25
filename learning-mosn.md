[mosn源码](https://qiankunli.github.io/2019/12/21/mosn_source.html)

打印日志
debug.PrintStack() 来查看某一个方法之前的调用栈。 再进一步，runtime.Caller 可以查看调用者所在源码文件与行号
// 一次获取一个调用者
// 0 表示当前函数，1 表示上一层函数，依次往上
if pc, file, line, ok := runtime.Caller(1); ok{
fmt.Println(runtime.FuncForPC(pc).Name(), file, line)
}
// 一次获取多个调用者
pc := make([]uintptr, 10)
n := runtime.Callers(1, pc)
for i := 0; i < n; i++ {
f := runtime.FuncForPC(pc[i])
file, line := f.FileLine(pc[i])
fmt.Printf("%s %d %s\n", file, line, f.Name())
}
fmt.Printf("==> %T\n",xx) 如果一个interface 有多个“实现类” 可以通过%T 查看struct 的类型
