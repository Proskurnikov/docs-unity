# Messenger и его использование

Скопировать Messenger

https://raw.githubusercontent.com/Proskurnikov/from-unity-wiki/main/Messenger.cs

Подготавливаем класс с именами для событий

```c sharp
namespace Events
{
    public static class StartupEvent
    {
        public const string MANAGERS_STARTED = "MANAGERS_STARTED";
        public const string MANAGERS_PROGRESS = "MANAGERS_PROGRESS";
    }
}
```

Слушателя чаще всего добавляем в методе `Awake` наследника `MonoBehaviour` (или там где это требуется). И не забываем отписаться в методе `OnDestroy` (или там где это требуется).

```c sharp
private void Awake() {
    Messenger<int, int>.AddListener(Events.StartupEvent.MANAGERS_PROGRESS, OnManagerProgress);
    Messenger.AddListener(Events.StartupEvent.MANAGERS_STARTED, OnManagerStarted);
}

private void OnDestroy() {
    Messenger<int, int>.RemoveListener(Events.StartupEvent.MANAGERS_PROGRESS, OnManagerProgress);
    Messenger.RemoveListener(Events.StartupEvent.MANAGERS_STARTED, OnManagerStarted);
}
```

Транслируем/выпускаем (broadcast) события (там где это требуется)

```c sharp
Messenger<int, int>.Broadcast(Events.StartupEvent.MANAGERS_PROGRESS, numReady,numModules);

Messenger.Broadcast(Events.StartupEvent.MANAGERS_STARTED);
```
