# react-query-server-state-management

What problem does React Query solve?

- `React Query` maintains cache of server data on client
- 它在客户端帮我们维护服务端的缓存
  - when you fetch server data, do it via `React Query`
  - 当你加载服务端数据时，需要通过它
- Your job: let `React Query` know when to refresh
- 你的任务就是：让它知道啥时候该刷新服务端数据
  - immediately, by invalidating data
  - 是立即就刷新吗？是的话你就直接让数据 **“失效”**
  - marking data as stale and configuraing refetch triggers
  - 然后它会讲数据标记为 “陈旧的”和重新触发请求服务端数据

> Bonnie Schulkin is a **Great Techer** ！
>
> Bonnie 讲得明明白白！
>
> 我也看过 `React Query` 作者自己出的教程，真心话还没 **Bonnie** 讲得明白！！

![001](images/001.png)
