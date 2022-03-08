# Сохранение данных

## PlayerPrefs

Сохранение

```c sharp
PlayerPrefs.SetFloat("speed", 1);
```

Получение (чтение)

```c sharp
PlayerPrefs.GetFloat("speed", 1);
```

Второй параметр при чтении - значение по умолчанию, в случае, если значение до этого не сохранено.

Подробнее в [документации](https://docs.unity3d.com/ScriptReference/PlayerPrefs.html)

## Serialize

```c sharp
public void SaveGameState() {
    Dictionary<string, object> gamestate = new Dictionary<string, object>();
    gamestate.Add("inventory", Managers.Inventory.GetData());
    gamestate.Add("health", Managers.Player.health);
    gamestate.Add("maxHealth", Managers.Player.maxHealth);
    gamestate.Add("curLevel", Managers.Mission.curLevel);
    gamestate.Add("maxLevel", Managers.Mission.maxLevel);
    FileStream stream = File.Create(_filename);
    BinaryFormatter formatter = new BinaryFormatter();
    formatter.Serialize(stream, gamestate);
    stream.Close();
}

public void LoadGameState() {
    if (!File.Exists(_filename)) {
        Debug.Log("No saved game");
        return;
    }
    Dictionary<string, object> gamestate;
    BinaryFormatter formatter = new BinaryFormatter();
    FileStream stream = File.Open(_filename, FileMode.Open);
    gamestate = formatter.Deserialize(stream) as Dictionary<string, object>;
    stream.Close();
    
    Managers.Inventory.UpdateData((Dictionary<string, int>) gamestate["inventory"]);
    Managers.Player.UpdateData((int)gamestate["health"], (int) gamestate["maxHealth"]);
    Managers.Mission.UpdateData((int)gamestate["curLevel"], (int) gamestate["maxLevel"]);
    Managers.Mission.RestartCurrent();
}
```
