# ApolloClient 3 <!-- .element: class="grey" -->

# Garbage collection

-----

- Garbage collection и возможность выборочной чистки кэша
  - Как работает GC? Начиная с ROOT_QUERY бежит вглубь собирая `__ref` в какой-нить Set. Вторым проходом пробегается по всем ключам в нормализованном кэше и удаляет те, которых нет в Set'е и в `retain`-set'е.
  - `cache.retain(id)` защитит запись от удаления из GC
  - `cache.release(id)` просто снимет отметку защиты от удаления в GC
  - `cache.evict(id)` сразу удалит запись из кэша (даже если запись защищена (`retain`))
- Хорошая тема, чтобы выкинуть Redux
