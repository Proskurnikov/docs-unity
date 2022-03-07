# Collider, RigidBody, CharacterController

## Что для чего используют

- Static Collider (У объекта есть только Collider, свойство isTrigger = false, без RigidBody) - стены, пол и другие неподвижные объекты

- Rigidbody Collider (У объекта есть Collider (свойство isTrigger = false) и RigidBody (свойство isKinematic = false)) незакрепленные (и из за этого подвижные) игровые объекты. Движение управляется физическим движком (как в реальном мире). Например, при столкновении с таким объектом, он подвинется. Можно использовать, например, для незакрепленного ящика. 

- Kinematic Rigidbody Collider (У объекта есть Collider (свойство isTrigger = false) и RigidBody (свойство isKinematic = true)). Можно использовать, например, для подвижной платформы, двери. Платформа не должна сдвигаться, если в неё упрёшься. Движением надо управлять через transform. Физический движок не управляет этой платформой.

- Trigger Collider (isTrigger = true). Все остальные не имеет смысла рассматривать отдельно (но они все равно перечислены ниже), т.к. если свойство isTrigger = true, то объекты проникают друг через друга, е если также хотя бы у одного объекта добавлен компонент RigidBody, то в момент столкновения вызывается метод OnTriggerEnter(). При пересечении с CharacterController RigidBody не обязателен.

  - Static Trigger Collider (У объекта есть только Collider, свойство isTrigger = true, без RigidBody)

  - Rigidbody Trigger Collider (У объекта есть Collider (свойство isTrigger = true) и RigidBody (свойство isKinematic = false))

  - Kinematic Rigidbody Trigger Collider (У объекта есть Collider (свойство isTrigger = true) и RigidBody (свойство isKinematic = true))

## Collider vs RigidBody

Книга Unity in Action (страница 131): Разница едва различимая, но важная:

- Collider определяет форму на которую воздействуют физические явления

- RigidBody определяет как ведет себя объект в физическом мире.

Эти компоненты остаются раздельными (хотя очень сильно связаны) потому, что многое объекты не нуждаются в физической симуляции, а нуждаются только в определении столкновений с другими объектами.

<https://answers.unity.com/questions/129796/rigidbodoy-vs-collider.html>

GameObject может иметь Collider без RigidBody. Unity считает что объект не двигается, если нет RigidBody. Unity не будет  просчитывать столкновения между  объектами, которые считаются неподвижными - это повышает производительность, если много объектов, с которыми есть возможность столкнуться. Кинематический RigidBody используется для движущихся объектов, которые могут сталкиваться с другими движущимися объектами (RigidBody) и неподвижными (Collider). В [документации](https://docs.unity3d.com/Manual/class-Rigidbody.html) же указано, что если два RigidBody сталкиваются, физический движок не просчитывает столкновение только если оба объекта не имеют Collider. RigidBody без коллайдера просто пройдут через друг друга.

<https://forum.unity.com/threads/rigidbody-vs-circle-collider-vs-box-collider.704909/>

Collider устанавливает границы вокруг объекта.
RigidBody как бы помещает объект в реальный мир (по ссылке это называют физической системой, физическим движком) - т.е. на объект влияют трение, скорость, силы которые к нему приложены.

## RigidBody vs Character Control

<https://medium.com/ironequal/unity-character-controller-vs-rigidbody-a1e243591483>

<https://www.mousawidev.com/blog/unity-character-controller-vs-rigidbody>

## Collider

Используется для неподвижных объектов, с которыми может столкнуться RigidBody.

<https://docs.unity3d.com/Manual/CollidersOverview.html>

## RigidBody

<https://docs.unity3d.com/Manual/class-Rigidbody.html5>

RigidBody позволяет объекту действовать под контролем физического движка  (как бы в реальном мире). Не будет работать без Collider.

## CharacterController

<https://docs.unity3d.com/Manual/class-CharacterController.html>
