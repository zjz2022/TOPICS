目前，在 Next.js 中操作数据库最流行的方式是使用 ORM 来操作数据库，而不是使用原始的 SQL 语句来操作数据库。使用原始 SQL 虽然可以完全控制数据库的操作，但是生产力会受到影响，因为将纯 SQL 字符串发送到数据库非常麻烦，并且会带来大量开销。

ORM 又叫**对象关系映射**，使用 ORM 来操作数据库不仅能**简化开发流程**、**提高代码可读性和可维护性**、**增强应用程序的灵活性和可移植性**，同时还能**防止SQL注入**。

因此在 Next.js 项目中我们采用 Prisma ORM 来集成 PostgreSQL 数据库。

但是并不是在所有场景下都建议使用 ORM 来操作数据库，如在需要执行复杂的数据库操作时，直接使用 SQL 可能更加高效和灵活。



作者：进击的松鼠
链接：https://juejin.cn/post/7366086988351406091
来源：稀土掘金
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。