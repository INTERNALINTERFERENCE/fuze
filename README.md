# ⚡ Fuze

A fault-tolerant, high-performance, and layered cache for Go, built for simplicity and resilience.

---

**Fuze** is more than just a cache. It's a smart caching framework that **fuses** a fast in-memory cache (L1) and a distributed cache (L2, e.g., Redis) into a single, seamless layer. It protects your application from system failures and cache stampedes, allowing you to write simpler, more robust, and highly performant code.

## 🤔 Why Fuze?

Have you ever found yourself...

-   Manually writing boilerplate to juggle an in-memory and a Redis cache?
-   Worrying that a Redis failure would overload your primary database and crash your service?
-   Dealing with inconsistent data because the local caches on your app's instances are out of sync?
-   Fighting cache stampedes where hundreds of requests try to regenerate the same cached item at once?

**Fuze solves these common, complex problems out of the box.** It acts like an electrical fuse: when a dependency fails, Fuze contains the blast radius, protecting your core systems from cascading failure.

---

## ✨ Features

-   **🗄️ Layered Caching (L1/L2):** Combines a high-speed in-memory cache with a scalable distributed cache for the best of both worlds.

-   **🛡️ Fault-Tolerance:** Continues to operate seamlessly even if the distributed cache goes down, serving stale data from memory to keep your application alive. This is the "fuse" mechanism.

-   **⚙️ Cache Stampede Protection:** Uses an industry-standard **`single-flight`** mechanism to ensure that only one request generates a value for an expired key, while others wait.

-   **🔄 Backplane Synchronization:** Keeps the in-memory caches across all your application instances consistent via a lightweight pub/sub message bus.

-   **✅ Fully Type-Safe:** Built from the ground up with Go Generics for a clean, safe, and ergonomic API. No more type assertions.

-   **🔌 Pluggable Architecture:** Easily implement your own **`DistributedCache`** or **`Backplane`** providers to support any backend.
