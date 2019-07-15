

# Services

> `Service` 是一个可以在后台执行长时间运行操作而不提供用户界面的应用组件。服务可由其他应用组件启动，而且即使用户切换到其他应用，服务仍将在后台继续运行。 此外，组件可以绑定到服务，以与之进行交互，甚至是执行进程间通信 (IPC)。 例如，服务可以处理网络事务、播放音乐，执行文件 I/O 或与内容提供程序交互，而所有这一切均可在后台进行。

## 基础知识

### 服务的形式

服务基本上分为两种形式：

- 启动

  当应用组件（如 Activity）通过调用 `startService()` 启动服务时，服务即处于“启动”状态。一旦启动，服务即可在后台无限期运行，即使启动服务的组件已被销毁也不受影响。 已启动的服务通常是执行单一操作，而且不会将结果返回给调用方。例如，它可能通过网络下载或上传文件。 操作完成后，服务会自行停止运行。

- 绑定

  当应用组件通过调用 `bindService()` 绑定到服务时，服务即处于“绑定”状态。绑定服务提供了一个客户端-服务器接口，允许组件与服务进行交互、发送请求、获取结果，甚至是利用进程间通信 (IPC) 跨进程执行这些操作。 仅当与另一个应用组件绑定时，绑定服务才会运行。 多个组件可以同时绑定到该服务，但全部取消绑定后，该服务即会被销毁。

### 服务和线程

简单地说，服务是一种即使用户未与应用交互也可在后台运行的组件。 因此仅在必要时才创建服务。

如需在主线程外部执行工作，不过只是在用户正在与应用交互时才有此需要，则应创建新线程而非服务。 例如，只是想在 Activity 运行的同时播放一些音乐，则可在 `onCreate()` 中创建线程，在 `onStart()` 中启动线程，然后在 `onStop()` 中停止线程。还可以考虑使用 `AsyncTask` 或 `HandlerThread`，而非传统的 `Thread` 类。如需了解有关线程的详细信息，请参阅[进程和线程](https://developer.android.com/guide/components/processes-and-threads.html#Threads)文档。

如果确实要使用服务，则默认情况下，它仍会在应用的主线程中运行，因此，如果服务执行的是密集型或阻止性操作，则应在服务内创建新线程。

##### 1231

```java
ic static final String COLUMN_USER_ID = "user_id";
        public static final String COLUMN_REAL_NAME = "real_name";
        public static final String COLUMN_SEX = "sex";
        public static final String COLUMN_BIRTHDAY = "birthday";
        public static final String COLUMN_ADDRESS = "address";
        public static final String COLUMN_EMERGENCY_PEOPLE = "emergency_people";
        public static final String COLUMN_EMERGENCY_TEL = "emergency_tel";
        public static final String COLUMN_TELEPHONE = "telephone";
    }
```

