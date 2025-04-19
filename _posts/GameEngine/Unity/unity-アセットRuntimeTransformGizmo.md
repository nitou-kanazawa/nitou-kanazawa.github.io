---
title: Runtime Transform Gizmos
categories: [ Unity ]
tags:
  - Unity
  - Unity AssetStore
  - Gizmos
---

## Runtime Transform Gizmos
 
[`RTG (Runtime Transform Gizmos)`](https://assetstore.unity.com/packages/tools/modeling/runtime-transform-gizmos-125537)は、ランタイム (ゲーム内) でトランスフォーム ギズモを簡単に組み込むことができるアセット．

- [API Docs](https://rtg.readthedocs.io/en/latest/#:~:text=RTG%20stands%20for%20Runtime%20Transform%20Gizmos%20and%20it,gizmos%20in%20your%20application%20at%20runtime%20%28i.e.%20in-game%29.)
- [Forum](https://discussions.unity.com/t/runtime-transform-gizmos-move-rotate-scale-universal-scene-gizmo-navigation-camera/714712)
- [Video Tutorials](https://www.youtube.com/watch?v=5i2m550eFyg&list=PLPwpt1oIEdwAY_Qo6fczi6qTiUjCMZBW1)

#### GizmoBehaviour 

RTGでは全ての

```cs
Gizmo gizmo = RTGizmoEngine.Get.CreateGizmo();
MoveGizmo moveGizmoBhv = gizmo.AddBehaviour<MoveGizmo>();
ObjectTransformGizmo transformGizmoBhv = gizmo.AddBehaviour<ObjectTransformGizmo>();
transformGizmoBhv.SetTransformChannelFlags(ObjectTransformGizmo.Channels.Position);
```


## 使い方




---
## 参考資料 


