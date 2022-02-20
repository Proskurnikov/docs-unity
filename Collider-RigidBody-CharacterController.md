# Collider, RigidBody, CharacterController

## Что для чего используют

Collider - для неподвижных объектов (стены, пол, //CHECK: деревья? и т.п.)

RigidBody - для подвижных игровых объектов (но также требует, что бы был Collider, иначе не будет учитывать столкновения) для имитации физических процессов реального мира (незакрепленные, подвижные игровые объекты, например, ящики и т.п.)

CharacterController - для основного персонажа (представляет из себя //CHECK: специально подготовленный Collider?. Требует самостоятельной реализации физических процессов - сила тяжести и т.п., что дает больший контроль)

Почему это так описано далее.

<!-- TODO: Сделать краткое описание, почему надо использовать именно для этих целей. -->

## Collider vs RigidBody

<https://answers.unity.com/questions/129796/rigidbodoy-vs-collider.html>

GameObject может иметь Collider без RigidBody. Unity считает что объект не двигается, если нет RigidBody. Unity не будет  просчитывать столкновения между  объектами, которые считаются неподвижными - это повышает производительность, если много объектов, с которыми есть возможность столкнуться. Кинематический RigidBody используется для движущихся объектов, которые могут сталкиваться с другими движущимися объектами (RigidBody) и неподвижными (Collider). В [документации](https://docs.unity3d.com/Manual/class-Rigidbody.html) же указано, что если два RigidBody сталкиваются, физический движок не просчитывает столкновение только если оба объекта не имеют Collider. RigidBody без коллайдера просто пройдут через друг друга.

<https://forum.unity.com/threads/rigidbody-vs-circle-collider-vs-box-collider.704909/>

Collider устанавливает границы вокруг объекта.
RigidBody как бы помещает объект в реальный мир (по ссылке это называют физической системой, физическим движком) - т.е. на объект влияют трение, скорость, силы которые к нему приложены.

<!-- TODO: Указано, что RigidBody может быть кинематическим или нет. Разобраться в чем разница -->

## RigidBody vs Character Control

<https://medium.com/ironequal/unity-character-controller-vs-rigidbody-a1e243591483>

<https://www.mousawidev.com/blog/unity-character-controller-vs-rigidbody>

## Collider

Используется для неподвижных объектов, с которыми может столкнуться RigidBody.

<https://docs.unity3d.com/Manual/CollidersOverview.html>

## RigidBody

<https://docs.unity3d.com/Manual/class-Rigidbody.html5>

RigidBody позволяет объекту действовать под контролем физического движка  (как бы в реальном мире).

## CharacterController

<https://docs.unity3d.com/Manual/class-CharacterController.html>
