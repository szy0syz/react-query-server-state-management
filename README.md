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

此次之外，还新增如下功能：

![002](images/002.png)

## First Project! Blog-em Ipsum

- Gets data from `https://jsonplaceholder.typicode.com/`
- Very simply, focus on React Query concepts
- 虽然很简单，但请专注于用 React Query 的概念来解决问题
  - Fetching data
  - Loading /error states
  - Reac Query dev tools
  - Pagination
  - Prefetching
  - Mutations

Getting Started

- Create query client
  - Client that manages queries and cache
- Apply Query Provider
  - Provides cache and client config to children
  - Takes query clients as the value
- Run useQuery
  - Hook that queries the server

isFetching vs. isLoading

![003](images/003.png)

Dev Tools

- Shows queries (by keys)
  - status of queryies
  - last updated timestamp
- Data explorer
- Query exporer

Stale  Data

- Why does it matter if the data is stale?
- 为什么说数据过期是重要的？
- Data refetch only triggers for stale data
- 其实数据重新加载只针对陈旧数据来触发
  - For example, component remount, window refocus
  - `staleTime` translates to "max age"
  - How to tolerate data potentially being out of date?
  - 如何容忍数据可能过期的情况？

Why is default staleTime set to 0?

![004](images/004.png)

- How is the data on the screen always up to date?
- is a much better question be asking than
- Why is my data not updating?

> 如何保证屏幕上的数据始终是最新的？
>
> 其实应该问：为什么我的数据不更新？ --> staleTime set to 0

staleTime vs. cacheTime

![005](images/005.png)

> 一个扫帚就能带代表这两者区别！配图是有点精髓！

- `staleTime` is for re-fetching
- Cache is for data the might be re-used later
  - query goes into "cold stroage" if there's no active `useQuery`
  - cache data expires after `cacheTime` (default: five minutes)
    - how long it's been since the last active `useQuery`
  - After the cache expores, the data is garbage collected
- Cache is backup data to display while fetching
